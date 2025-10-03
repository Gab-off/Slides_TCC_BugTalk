<script setup>
import { Pie } from 'vue-chartjs';
import { Chart as ChartJS, Title, Tooltip, Legend, ArcElement, CategoryScale } from 'chart.js';
import { computed } from 'vue';

// 1. Registra os elementos necessários para o Chart.js
ChartJS.register(Title, Tooltip, Legend, ArcElement, CategoryScale);

// 2. Define as propriedades que o componente aceita
// :clicks="$clicks" -> o contador de cliques atual do slide
// :start-at="N" -> o número do clique em que este componente deve aparecer
const props = defineProps({
  clicks: {
    type: Number,
    default: 0
  },
  startAt: {
    type: Number,
    default: 0
  }
});

// 3. Define os dados e cores do gráfico
const LABELS_ORIGINAIS = ['Sim, com frequência', 'Às vezes', 'Raramente', 'Nunca'];
const DADOS_ORIGINAIS = [46.9, 46.9, 3.1, 3.1];
const CORES_ORIGINAIS = ['#36A2EB', '#FF6384', '#FFCE56', '#4BC0C0'];
const COR_DESTACADA_PRINCIPAL = '#28a745';
const COR_INATIVA = '#cccccc';

// 4. LÓGICA PRINCIPAL: Calcula os cliques relativos ao componente
// Isso faz com que a animação interna do gráfico só comece APÓS ele aparecer no slide.
const relativeClicks = computed(() => {
  if (props.clicks >= props.startAt) {
    return props.clicks - props.startAt;
  }
  return -1; // Indica que o componente ainda não está "ativo"
});

// 5. Define os dados do gráfico com base nos cliques relativos
const chartData = computed(() => {
  // A transição para o estado final acontece no PRIMEIRO clique relativo.
  // relativeClicks.value será 0 quando o gráfico aparecer, e 1 no clique seguinte.
  if (relativeClicks.value < 1) {
    // Estado inicial
    return {
      labels: LABELS_ORIGINAIS,
      datasets: [{ backgroundColor: CORES_ORIGINAIS, data: DADOS_ORIGINAIS }]
    };
  } else {
    // Estado final
    const somaDificuldade = DADOS_ORIGINAIS[0] + DADOS_ORIGINAIS[1];
    const outros = DADOS_ORIGINAIS[2] + DADOS_ORIGINAIS[3];
    return {
      labels: ['Já teve dificuldade', 'Não teve ou raramente teve'],
      datasets: [{ backgroundColor: [COR_DESTACADA_PRINCIPAL, COR_INATIVA], data: [somaDificuldade, outros] }]
    };
  }
});

// 6. Define as opções do gráfico (título, animação, cores dos textos, etc.)
const chartOptions = computed(() => ({
  responsive: true,
  maintainAspectRatio: false,
  animation: {
    duration: 800,
    easing: 'easeInOutCubic'
  },
  plugins: {
    title: {
      display: true,
      text: 'Você já teve dificuldade em encontrar ajuda para dúvidas durante os estudos?',
      font: { size: 20 },
      color: '#FFFFFF' // Cor do título do gráfico
    },
    legend: {
      position: 'top',
      labels: {
        color: '#E0E0E0' // Cor das legendas (Raramente, Nunca, etc.)
      }
    },
    tooltip: {
      callbacks: {
        label: function(context) {
          let label = context.label || '';
          if (label) { label += ': '; }
          if (context.parsed !== null) { label += context.parsed + '%'; }
          return label;
        }
      }
    }
  }
}));

// 7. Propriedades computadas para controlar a visibilidade de cada parte
const isComponentVisible = computed(() => relativeClicks.value >= 0);
const showInitialText = computed(() => relativeClicks.value === 0);
const showFinalText = computed(() => relativeClicks.value >= 1);

</script>

<template>
  <div
      class="w-full h-full flex flex-col justify-center items-center p-8 transition-opacity duration-500"
      :class="[isComponentVisible ? 'opacity-100' : 'opacity-0']"
  >


    <div class="flex-grow flex justify-center items-center w-full h-full min-h-0">
      <Pie
          :data="chartData"
          :options="chartOptions"
          class="max-w-full max-h-full"
      />
    </div>

    <p
        class="text-2xl font-bold text-green-500 mt-8 text-center transition-opacity duration-500"
        :class="[showFinalText ? 'opacity-100' : 'opacity-0']"
    >
      {{ (DADOS_ORIGINAIS[0] + DADOS_ORIGINAIS[1]).toFixed(1) }}% já teve dificuldade em encontrar ajuda!
    </p>
  </div>
</template>
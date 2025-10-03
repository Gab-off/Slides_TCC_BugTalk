<script setup>
import { Bar } from 'vue-chartjs';
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js';

// 1. Registra os elementos necessários do Chart.js
ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale);

// 2. Define os dados do gráfico (exemplo)
const chartData = {
  labels: ['Jan', 'Fev', 'Mar', 'Abr', 'Mai'],
  datasets: [
    {
      label: 'Vendas (em K)',
      backgroundColor: '#007ACC', // Cor primária do WebStorm :)
      data: [40, 20, 12, 50, 65],
    }
  ]
};

// 3. Define as opções do gráfico (exemplo: desativa a responsividade e mantém o título)
const chartOptions = {
  responsive: true,
  maintainAspectRatio: false,
  plugins: {
    title: {
      display: true,
      text: 'Desempenho Trimestral'
    }
  }
};
</script>

<template>
  <div class="w-full h-full flex justify-center items-center p-8">
    <Bar
        :data="chartData"
        :options="chartOptions"
        class="w-full h-full"
    />
  </div>
</template>
---
# You can also start simply with 'default'
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
layout: cover
background: '#000'
# some information about your slides (markdown enabled)
title: ByteBridge
info: |
  Slides de apresentação da empresa ByteBridge
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
---

   <h1 class="font-bold"><span class="text-[#ff7b00]">Byte</span>Bridge</h1>
    <p></p>
    <p class=" text-2xl inline-block px-4 py-2 rounded-xl bg-[#ff7b00]">Conectando usuários a tecnologia</p>

<img class="absolute -bottom-30 -left-10" src="/images/detail_1.svg">
<img class="absolute -top-30 -right-10" src="/images/detail_1.svg">

[//]: # (Presentation slides for developers)

[//]: # ()

[//]: # (<div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">)

[//]: # (  Press Space for next page <carbon:arrow-right />)

[//]: # (</div>)

[//]: # ()

[//]: # (<div class="abs-br m-6 text-xl">)

[//]: # (  <button @click="$slidev.nav.openInEditor" title="Open in Editor" class="slidev-icon-btn">)

[//]: # (    <carbon:edit />)

[//]: # (  </button>)

[//]: # (  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">)

[//]: # (    <carbon:logo-github />)

[//]: # (  </a>)

[//]: # (</div>)

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: full
class: background-black_logo
transition: slide-up
---


<h1 class="mt-5 font-bold">Integ<span class="text-[#f27e14]">rantes</span></h1>
<div v-click class="flex flex-col items-start mt-10">
    <p class="border-b pb-2 border-[#d56801]">Gabriel de Miranda Albuquerque</p>
    <p class="border-b pb-2 border-[#d56801]">Jonas Santana dos Santos</p>
    <p class="border-b pb-2 border-[#d56801]">Gilberto Batista de Alencar</p>
    <p class="border-b pb-2 border-[#d56801]">Vinicius de Queiroz Moretto Silva</p>
    <p class="border-b pb-2 border-[#d56801]">Gabryel Mendes Candido</p>
</div>

<img class="absolute rotate-45 opacity-50 -bottom-15 -left-10" src="/images/detail_2.svg">



<!--
Here is another comment.
-->


---
layout: full
class: bg-black
transition: slide-up
clicks: 4
---

<h1 class="font-bold mt-20">ByteBridge <span class="text-[#d98b1d]">Studio</span></h1>

<div class="grid grid-cols-3 text-center gap-4 mt-10">
    <div class="transition-opacity duration-500" 
         :class="{
            'opacity-100': $clicks === 1 || $clicks >= 4,
            'opacity-0': !($clicks === 1 || $clicks >= 4)
         }">
        <h2 class="font-semibold text-lg border border-orange-500 rounded-full px-3 py-1">Missão</h2>
        <p class="mt-4 pgf">Capacitar indivíduos e comunidades com ferramentas digitais inovadoras.</p>
    </div>
    <div class="transition-opacity duration-500"
         :class="{
            'opacity-100': $clicks === 2 || $clicks >= 4,
            'opacity-0': !($clicks === 2 || $clicks >= 4)
         }">
        <h2 class="font-semibold border border-orange-500 rounded-full px-3 py-1">Visão</h2>
        <p class="mt-4 pgf">Ser líder global em inovação conectando tecnologia, educação e bem-estar.</p>
    </div>
    <div class="transition-opacity duration-500"
         :class="{
            'opacity-100': $clicks === 3 || $clicks >= 4,
            'opacity-0': !($clicks === 3 || $clicks >= 4)
         }">
        <h2 class="font-semibold border border-orange-500 rounded-full px-3 py-1 ">Valores</h2>
        <p class="mt-4 pgf">Ética, acessibilidade e colaboração.</p>
    </div>
</div>

<img class="absolute rotate-45 opacity-50 -bottom-15 -left-10" src="/images/detail_2.svg">
<img class="absolute rotate-45 opacity-50 -top-15 -right-10" src="/images/detail_2.svg">



<style>
h1 {
    text-align: center;
font-size: 2.5rem;
}

.pgf {
font-size: 1.3rem;
}

</style>
---
layout: iframe
background: background-black
url: https://gab-off.github.io/byteBridgeSite/
---

---
layout:
class: bg-black

# Opcional, o Slidev calcula o máximo de cliques, mas é bom manter para clareza

clicks: 5
---

<h1 class="font-bold">Apresentação do <span class="
    text-5xl font-extrabold 
    bg-gradient-to-r from-[#96C473] to-[#026E4A]
    bg-clip-text 
    text-transparent
">cenário</span></h1>
<ul class="">
    <li class="text-larger" v-click>Necessidade de espaços de diálogo e colaboração na ETEC</li>
    <li class="text-larger" v-click>Alunos de DS carecem de ambiente estruturado para dúvidas e trocas de conhecimento.
</li>
    <li class="text-larger" v-click>46,9% dos alunos pesquisados já tiveram dificuldades em encontrar ajuda
</li>
</ul>
<div v-click class="h-80 border-1 border-[#4E945D] rounded-2xl mt-5">
    <MeuGraficoDeDuvidas :clicks="$clicks" :start-at="4" />
</div>


<img class="absolute rotate-45 opacity-50 -bottom-15 -left-10" src="/images/detail_green.svg">
<img class="absolute rotate-45 opacity-50 -top-15 -right-10" src="/images/detail_green.svg">


<style>
.text-larger {
    font-size: 1.2rem;
}
</style>

---
layout: full
class: bg-black
---

<h1 class="font-bold pb-10 flex gap-3  mt-20">
Problemas<span class="text-[#35B89F]">identificados</span>
</h1>

<div class="grid grid-cols-2 gap-5">
    <div v-click>
        <h2 class="rounded-3xl px-3 py-1 bg-gradient-to-r from-[#33B49D] to-[#005870]">Comunicação</h2>
        <ul>
            <li class="topico">Ausência de um ambiente colaborativo centralizado.</li>
            <li class="topico">Falta de comunicação entre diferentes módulos e turmas.</li>
            <li class="topico">Falta de incentivo à colaboração contínua.</li>
        </ul>
    </div>
    <div v-click>
        <h2 class="rounded-3xl px-3 py-1 bg-gradient-to-r from-[#33B49D] to-[#005870]">Ambiente</h2>
        <ul>
            <li class="topico">Ausência de um ambiente colaborativo centralizado.</li>
            <li class="topico">Falta de comunicação entre diferentes módulos e turmas.</li>
            <li class="topico">Falta de incentivo à colaboração contínua.</li>
        </ul>
    </div>
</div>

<style>
    .topico {
        font-size: 1.2rem;
    }   
</style>

---
layout: center
class: bg-black
---

<h1 class="title font-bold">Solução <span class="color-[#08a3c1]">Proposta</span></h1>
<h2 v-click class="content text-center font-bold">Bug<span class="color-[#08a3c1]">Talk</span></h2>

<style>
    .title {
        font-size: 2.5rem;    
    }

    .content {
        font-size: 3rem;
    }
</style>

---
layout: center
class: bg-black
---

<h1 class="font-bold">Considerações <span class="color-[#08a3c1]">finais</span></h1>
<template>
  <div class="space-y-6">
    <NuxtImg src="https://github.com/joao-tambue.png" alt="João Tambue"
      class="ring-2 border ring-gray-200 border-gray-300 dark:ring-white/10 dark:border-gray-800 hover:ring-4 transition-all duration-300 bg-gray-200 dark:bg-gray-900 rounded-full h-12 w-12 sm:h-16 sm:w-16"
      sizes="48px sm:64px" placeholder format="webp" />
    <h1 class="text-xl font-bold tracking-tight text-gray-800 dark:text-gray-100">
      Hello!
    </h1>
    <p class="text-gray-900 dark:text-gray-400">
      Sou o João Tambue, Frontend Software Engineer de Luanda, Angola. Tenho
      experiência no desenvolvimento de aplicações web e mobile com React,
      Vue.js, React Native, TypeScript e JavaScript, construindo interfaces
      orientadas à experiência do utilizador, escaláveis e performáticas, e
      colaborando com equipas multidisciplinares através de code reviews e
      boas práticas de desenvolvimento.
    </p>
    <p class="text-gray-900 dark:text-gray-400">
      Tenho experiência com integração de APIs, arquiteturas modernas, testes
      automatizados e uso de Inteligência Artificial para acelerar ciclos de
      desenvolvimento e aumentar a produtividade. Fora do trabalho, gosto de
      participar em desafios de tecnologia e inovação.
    </p>
  </div>
</template>

<script setup>
useSeoMeta({
  title: "João Tambue",
  description:
    "João Tambue, Frontend Software Engineer de Luanda, Angola. Desenvolvimento de aplicações web e mobile com React, Vue.js, React Native, TypeScript e JavaScript.",
});
</script>

<template>
  <main class="min-h-screen">
    <AppHeader class="mb-12" title="Experience" :description="description" />
    <div class="space-y-8">
      <AppExperienceCard
        v-for="(experience, id) in experiences"
        :key="id"
        :experience="experience"
      />
    </div>
  </main>
</template>

<script setup>
const description =
  "A minha trajetória profissional como Frontend & Mobile Developer — empresas, projetos e desafios em que trabalhei.";
useSeoMeta({
  title: "Experience | João Tambue",
  description,
});

const { data: experiences } = await useAsyncData("experience-all", () =>
  queryContent("/experience").find()
);
</script>

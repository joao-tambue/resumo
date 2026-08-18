<template>
  <main class="min-h-screen">
    <AppHeader class="mb-12" :title="t('projects.pageTitle')" :description="t('projects.pageDescription')" />
    <div class="space-y-4">
      <AppProjectCard
        v-for="(project, id) in projects"
        :key="id"
        :project="project"
      />
    </div>
  </main>
</template>

<script setup>
const { t } = useI18n();
useSeoMeta({
  title: () => `${t("projects.pageTitle")} | João Tambue`,
  description: () => t("projects.pageDescription"),
});

const { data: projects } = await useAsyncData("projects-all", () =>
  queryContent("/projects").find()
);
</script>

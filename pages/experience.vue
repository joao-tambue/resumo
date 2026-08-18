<template>
  <main class="min-h-screen">
    <AppHeader class="mb-12" :title="t('experience.pageTitle')" :description="t('experience.pageDescription')" />
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
const { t } = useI18n();
useSeoMeta({
  title: () => `${t("experience.pageTitle")} | João Tambue`,
  description: () => t("experience.pageDescription"),
});

const { data: experiences } = await useAsyncData("experience-all", () =>
  queryContent("/experience").find()
);
</script>

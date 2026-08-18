<template>
  <div>
    <h2 class="uppercase text-xs font-semibold text-gray-400 mb-6">
      {{ t("projects.sectionTitle") }}
    </h2>
    <div class="space-y-4">
      <AppProjectCard
        v-for="(project, id) in projects"
        :key="id"
        :project="project"
      />
    </div>
    <div class="flex items-center justify-center mt-6 text-sm">
      <UButton
        :label="t('projects.viewAll')"
        :to="localePath('/projects')"
        variant="link"
        color="gray"
      />
    </div>
  </div>
</template>

<script lang="ts" setup>
const { t } = useI18n();
const localePath = useLocalePath();

const { data: projects } = await useAsyncData("projects-home", () =>
  queryContent("/projects").limit(3).find()
);
</script>

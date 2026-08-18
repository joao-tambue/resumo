<template>
  <article class="p-2 -m-2 rounded-lg">
    <div class="flex items-end gap-4">
      <div class="max-w-sm">
        <h3 class="text-sm font-medium">
          {{ project.name }}
        </h3>
        <p class="text-gray-400 text-sm">{{ project.description }}</p>
      </div>
      <div
        class="flex-1 border-b border-dashed border-gray-300 dark:border-gray-800"
      ></div>
      <UAvatar
        :src="project.thumbnail"
        :ui="{ rounded: 'rounded z-10 relative' }"
        size="md"
        :alt="project.name"
      />
    </div>

    <div v-if="expanded" class="mt-3 space-y-3">
      <div v-if="project.technologies?.length" class="flex flex-wrap gap-1.5">
        <span
          v-for="tech in project.technologies"
          :key="tech"
          class="text-xs px-2 py-0.5 rounded-full bg-gray-100 dark:bg-white/10 text-gray-600 dark:text-gray-300"
        >
          {{ tech }}
        </span>
      </div>
      <p v-if="project.impact" class="text-sm text-gray-500 dark:text-gray-400">
        <span class="font-medium text-gray-700 dark:text-gray-300">{{ t("projects.impact") }}:</span>
        {{ project.impact }}
      </p>
      <div class="flex items-center gap-4 text-sm">
        <NuxtLink
          v-if="project.github"
          :to="project.github"
          target="_blank"
          external
          class="inline-flex items-center gap-1.5 text-primary-600 hover:text-primary-500 dark:text-primary-400"
        >
          <Icon name="mdi:github" class="w-4 h-4" />
          {{ t("projects.github") }}
        </NuxtLink>
        <NuxtLink
          v-if="project.demo"
          :to="project.demo"
          target="_blank"
          external
          class="inline-flex items-center gap-1.5 text-primary-600 hover:text-primary-500 dark:text-primary-400"
        >
          <Icon name="heroicons:arrow-top-right-on-square" class="w-4 h-4" />
          {{ t("projects.demo") }}
        </NuxtLink>
        <span v-if="!project.github && !project.demo" class="text-xs text-gray-400">
          {{ t("projects.privateRepo") }}
        </span>
      </div>
    </div>

    <button
      v-if="hasDetails"
      type="button"
      class="mt-2 text-xs font-medium text-primary-600 hover:text-primary-500 dark:text-primary-400"
      @click="expanded = !expanded"
    >
      {{ expanded ? t("common.seeLess") : t("common.seeMore") }}
    </button>
  </article>
</template>

<script setup>
const props = defineProps({
  project: {
    type: Object,
    required: true,
  },
});

const { t } = useI18n();
const expanded = ref(false);

const hasDetails = computed(() =>
  Boolean(
    props.project.technologies?.length ||
      props.project.impact ||
      props.project.github ||
      props.project.demo
  )
);
</script>

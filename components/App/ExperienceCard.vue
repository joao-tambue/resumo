<template>
  <article class="flex gap-4">
    <div class="flex-none pt-1">
      <UAvatar
        :alt="experience.company"
        :ui="{ rounded: 'rounded z-10 relative' }"
        size="md"
      />
    </div>
    <div class="min-w-0 flex-1">
      <div class="flex flex-wrap items-baseline gap-x-2">
        <h3 class="text-sm font-medium text-gray-800 dark:text-gray-100">
          {{ experience.role }}
        </h3>
        <span class="text-sm text-gray-400">&middot; {{ experience.company }}</span>
      </div>
      <time class="text-xs text-gray-400 dark:text-gray-600">
        {{ experience.period }}
      </time>
      <p class="text-gray-400 text-sm mt-2">{{ experience.description }}</p>

      <ul
        v-if="expanded && experience.highlights?.length"
        class="mt-3 space-y-1.5 list-disc list-outside pl-4 text-gray-400 text-sm"
      >
        <li v-for="(highlight, i) in experience.highlights" :key="i">
          {{ highlight }}
        </li>
      </ul>

      <button
        v-if="experience.highlights?.length"
        type="button"
        class="mt-2 text-xs font-medium text-primary-600 hover:text-primary-500 dark:text-primary-400"
        @click="expanded = !expanded"
      >
        {{ expanded ? t("common.seeLess") : t("common.seeMore") }}
      </button>
    </div>
  </article>
</template>

<script setup>
defineProps({
  experience: {
    type: Object,
    required: true,
  },
});

const { t } = useI18n();
const expanded = ref(false);
</script>

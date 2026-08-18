<script setup>
const { locale, t } = useI18n();
const switchLocalePath = useSwitchLocalePath();

const otherLocale = computed(() => (locale.value === "pt" ? "en" : "pt"));
</script>

<template>
  <UTooltip :text="t('locale.switch')" :ui="{ popper: { strategy: 'absolute' } }">
    <NuxtLink
      :to="switchLocalePath(otherLocale)"
      class="relative px-3 py-4 flex items-center justify-center transition hover:text-primary-500 dark:hover:text-primary-400 text-xs font-semibold uppercase"
    >
      {{ otherLocale }}
      <span class="sr-only">{{ t("locale.switch") }}</span>
    </NuxtLink>
  </UTooltip>
</template>

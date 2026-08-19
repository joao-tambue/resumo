<script setup>
const { locale, locales, t } = useI18n();
const switchLocalePath = useSwitchLocalePath();

const items = computed(() => [
  locales.value.map((l) => ({
    label: `${l.flag ?? ""} ${l.name}`.trim(),
    icon: l.code === locale.value ? "heroicons:check" : undefined,
    to: switchLocalePath(l.code),
  })),
]);
</script>

<template>
  <UDropdown :items="items" :popper="{ placement: 'bottom-end', strategy: 'absolute' }">
    <UTooltip :text="t('locale.switch')" :ui="{ popper: { strategy: 'absolute' } }">
      <button
        class="relative px-3 py-4 flex items-center justify-center transition hover:text-primary-500 dark:hover:text-primary-400"
      >
        <Icon name="heroicons:globe-alt" class="w-5 h-5" />
        <span class="sr-only">{{ t("locale.switch") }}</span>
      </button>
    </UTooltip>

    <template #item="{ item }">
      <span class="truncate">{{ item.label }}</span>
      <Icon
        v-if="item.icon"
        :name="item.icon"
        class="w-4 h-4 ms-auto flex-shrink-0 text-primary-500"
      />
    </template>
  </UDropdown>
</template>

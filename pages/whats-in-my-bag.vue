<template>
  <main class="min-h-screen">
    <AppHeader
      class="mb-12"
      :title="t('bag.pageTitle')"
      :description="t('bag.pageDescription')"
    />
    <div class="space-y-24">
      <ul class="space-y-8">
        <AppUsesHeader :title="t('bag.hardware')" />
        <AppUsesItem v-for="(item, id) in hardware" :key="id" :item="item" />
      </ul>
      <ul class="space-y-8">
        <AppUsesHeader :title="t('bag.software')" />
        <AppUsesItem v-for="(item, id) in software" :key="id" :item="item" />
      </ul>
      <ul class="space-y-8">
        <AppUsesHeader :title="t('bag.desk')" />
        <AppUsesItem v-for="(item, id) in desk" :key="id" :item="item" />
      </ul>
      <ul class="space-y-8">
        <AppUsesHeader :title="t('bag.other')" />
        <AppUsesItem v-for="(item, id) in other" :key="id" :item="item" />
      </ul>
    </div>
  </main>
</template>

<script setup>
const { t } = useI18n();
useSeoMeta({
  title: () => `${t("bag.pageTitle")} | João Tambue`,
  description: () => t("bag.pageDescription"),
});
const { data: items } = await useAsyncData("uses", () =>
  queryContent("/uses").find()
);
const hardware = items.value.filter((item) => item.category === "hardware");
const software = items.value.filter((item) => item.category === "software");
const desk = items.value.filter((item) => item.category === "desk");
const other = items.value.filter((item) => item.category === "others");
</script>

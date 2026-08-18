<template>
  <main class="min-h-screen">
    <AppHeader class="mb-16" :title="t('articles.pageTitle')" :description="t('articles.pageDescription')" />
    <ul class="space-y-16">
      <li v-for="(article, id) in articles" :key="id">
        <AppArticleCard :article="article" />
      </li>
    </ul>
  </main>
</template>

<script setup>
const { t } = useI18n();
useSeoMeta({
  title: () => `${t("articles.pageTitle")} | João Tambue`,
  description: () => t("articles.pageDescription"),
});

const { data: articles } = await useAsyncData("all-articles", () =>
  queryContent("/articles").sort({ published: -1 }).find()
);
</script>

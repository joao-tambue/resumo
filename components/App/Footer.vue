<template>
  <footer
    class="max-w-2xl mx-auto text-gray-400 dark:text-gray-600 text-sm text-center pb-8"
  >
    <br>
    <p>{{ t("footer.rights", { year: currentYear }) }}</p>
  </footer>
</template>

<script setup>
const { t } = useI18n();
const currentYear = new Date().getFullYear();
</script>

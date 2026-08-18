<template>
  <div>
    <h2 class="uppercase text-xs font-semibold text-gray-400 mb-6">
      EXPERIENCE
    </h2>
    <div class="space-y-6">
      <AppExperienceCard
        v-for="(experience, id) in experiences"
        :key="id"
        :experience="experience"
      />
    </div>
    <div class="flex items-center justify-center mt-6 text-sm">
      <UButton
        label="Full Experience &rarr;"
        to="/experience"
        variant="link"
        color="gray"
      />
    </div>
  </div>
</template>

<script lang="ts" setup>
const { data: experiences } = await useAsyncData("experience-home", () =>
  queryContent("/experience").limit(2).find()
);
</script>

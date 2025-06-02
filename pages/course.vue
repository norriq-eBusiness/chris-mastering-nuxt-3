<script lang="ts" setup>
const { chapters } = useCourse();
</script>

<template>
  <div
    class="p-12 bg-gray-100 w-full h-full min-h-screen flex flex-col items-center"
  >
    <div class="prose mb-12">
      <h1>
        <span class="font-medium">
          Course:
          <span class="font-bold">Mastering Nuxt 3</span>
        </span>
      </h1>
    </div>

    <div class="flex justify-center w-full max-w-[1500px]">
      <div
        class="prose mr-4 p-8 bg-white rounded-md w-fit min-w-[20%] flex flex-col"
      >
        <h3>Chapters</h3>
        <div
          class="space-y-1 mb-4 flex flex-col"
          v-for="chapter in chapters"
          :key="chapter.slug"
        >
          <h4>{{ chapter.title }}</h4>
          <NuxtLink
            v-for="(lesson, index) in chapter.lessons"
            :to="lesson.path"
            :key="lesson.slug"
            class="flex space-x-1 no-underline prose-sm"
            :class="
              lesson.path === $route.fullPath
                ? 'text-orange-600'
                : 'text-gray-600'
            "
          >
            <span>{{ index + 1 }}. {{ lesson.title }}</span>
          </NuxtLink>
        </div>
      </div>

      <div class="p-12 bg-white rounded-md w-full">
        <NuxtPage />
      </div>
    </div>
  </div>
</template>

<style scoped></style>

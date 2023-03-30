<template>
  <NuxtLayout>
    <div class="flex flex-col">
      <div v-if="error.statusCode === '404'" class="prose">
        <h1>404</h1>
        <p>It looks like that doesn't exist.</p>
        <p>Sorry!</p>
      </div>
      <div v-else class="prose">
        <h1>Dang</h1>
        <p>It looks like something broke.</p>
        <p>Sorry!</p>
      </div>
      <div class="prose mt-5">
        <p>
          <strong>{{ error.message }}</strong>
        </p>
        <p>
          Go to the
          <a
              @click="handleError"
              class="hover:cursor-pointer">
            first lesson.
          </a>
        </p>
      </div>
    </div>
  </NuxtLayout>
</template>

<script setup>
const error = useError();

const handleError = () => {
  clearError({
    redirect:
      '/course/chapter/1-chapter-1/lesson/1-introduction-to-typescript-with-vue-js-3'
  })
}
</script>
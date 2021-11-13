<template>
  <div class="mx-auto text-center max-w-4xl">
    <h1 class="text-4xl" v-if="error.statusCode === 404">404</h1>
    <h1 v-else>An error occurred</h1>
    <NuxtLink class="text-center" to="/">Home page</NuxtLink>
  </div>
</template>

<script>
export default {
  props: ["error"],
  layout: "error", // you can set a custom layout for the error page
};
</script>
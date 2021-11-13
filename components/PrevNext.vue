<template>
  <div class="flex justify-between mt-6">
    <NuxtLink
      v-if="prev"
      :to="{ name: 'article-slug', params: { slug: prev.slug } }"
      class="font-bold px-4 py-2 bg-gray-900 text-white rounded hover:underline"
    >
      &larr; {{ prev.title }}
    </NuxtLink>
    <span v-else>&nbsp;</span>
    <NuxtLink
      v-if="next"
      :to="{ name: 'article-slug', params: { slug: next.slug } }"
      class="font-bold px-4 py-2 bg-gray-900 text-white rounded hover:underline"
    >
      {{ next.title }} &rarr;
    </NuxtLink>
    <span v-else>&nbsp;</span>
  </div>
</template>

<script>
export default {
  props: {
    prev: {
      type: Object,
      default: () => null,
    },
    next: {
      type: Object,
      default: () => null,
    },
  },
};
</script>
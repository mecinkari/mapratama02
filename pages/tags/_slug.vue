<template>
  <div class="py-5 max-w-xl mx-auto">
    <h1 class="text-4xl font-bold">
      Tag: <span class="text-blue-600 underline">#{{ slug }}</span>
    </h1>
    <hr class="border my-4" />
    <div class="flex flex-col gap-y-4">
      <article v-for="article in articles" :key="article" class="p-5 shadow">
        <div class="mb-3">
          <nuxt-link
            class="p-1 text-sm rounded mr-2 text-blue-600 font-bold bg-blue-50"
            v-for="tag in article.tags"
            :key="tag"
            :to="`/tags/${tag}`"
          >
            #{{ tag }}
          </nuxt-link>
        </div>
        <nuxt-link
          class=""
          :to="{ name: 'article-slug', params: { slug: article.slug } }"
        >
          <p class="text-2xl font-bold hover:text-blue-600">
            {{ article.title }}
          </p>
        </nuxt-link>
        <p>{{ article.desc }}</p>
        <p class="text-right">Created by: {{ article.author }}</p>
      </article>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const articles = await $content("blog")
      .only(["title", "desc", "author", "slug", "tags"])
      .sortBy("createdAt", "asc")
      .where({ tags: { $contains: params.slug } })
      .fetch();
    const slug = params.slug;
    return { articles, slug };
  },
};
</script>

<style>
</style>
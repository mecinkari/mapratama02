<template>
  <div class="py-5 max-w-6xl px-6 mx-auto">
    <div class="text-center">
      <h1 class="text-4xl font-bold">Mapratama02 Site</h1>
      <p class="leading-10 text-gray-500 font-semibold">
        Selamat datang di website saya
      </p>
    </div>
    <hr class="border my-4" />
    <p class="text-3xl text-center">Postingan terakhir</p>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-2 mt-4">
      <article
        v-for="article in articles"
        :key="article"
        class="p-5 border rounded"
      >
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
      </article>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const articles = await $content("blog", params.slug)
      .limit(3)
      .only(["title", "desc", "author", "slug", "tags"])
      .sortBy("createdAt", "asc")
      .where({ status: "published" })
      .fetch();

    return { articles };
  },
};
</script>

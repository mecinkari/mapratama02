<template>
  <div class="py-5 max-w-6xl px-6 mx-auto">
    <p class="text-4xl font-bold">Tulisan Terbaru</p>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-2 mt-4">
      <article
        v-for="article in articles"
        :key="article.slug"
        class="p-5 border rounded bg-white"
      >
        <nuxt-img
          class="rounded-lg"
          v-if="article.img"
          :src="`assets/blog/${article.img}`"
          preset="preview"
        />
        <img
          class="rounded-lg"
          v-else
          src="https://via.placeholder.com/1024x768/eee?text=4:3"
        />
        <p class="text-sm mt-2 text-gray-500">
          {{ formatDate(article.createdAt) }}
        </p>
        <div class="my-3">
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
      .sortBy("createdAt", "desc")
      .where({ status: "published" })
      .fetch();

    return { articles };
  },
  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("id", options);
    },
  },
};
</script>

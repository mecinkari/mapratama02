<template>
  <div class="py-5 px-6 container mx-auto">
    <h1 class="text-4xl font-bold">Blog</h1>
    <hr class="border my-4" />
    <div class="grid grid-cols-1 md:grid-cols-3 md:gap-x-4 gap-y-4">
      <article
        v-for="article in articles"
        :key="article"
        class="p-5 border block w-full bg-white rounded"
      >
        <div class="mb-3">
          <div class="aspect-w-16 aspect-h-9">
            <img
              class="
                w-full
                h-full
                object-center object-cover
                lg:w-full lg:h-full
              "
              v-if="article.mainImage.asset.url"
              :src="`${article.mainImage.asset.url}`"
            />
            <img
              class="rounded-lg"
              v-else
              src="https://via.placeholder.com/1024x768/eee?text=4:3"
            />
          </div>
        </div>
        <div class="mb-3">
          <nuxt-link
            class="p-1 text-sm rounded mr-2 text-blue-600 font-bold bg-blue-50"
            v-for="category in article.categories"
            :key="category.id"
            :to="`/tags/${category.title}`"
          >
            #{{ category.title }}
          </nuxt-link>
        </div>
        <p class="text-sm text-gray-500">
          {{ formatDate(article.publishedAt) }}
        </p>
        <nuxt-link
          class=""
          :to="{ name: 'article-slug', params: { slug: article.slug.current } }"
        >
          <p class="text-2xl font-bold hover:text-blue-600">
            {{ article.title }}
          </p>
          <!-- <nuxt-content :document="{ body: article.excerpt }" /> -->
        </nuxt-link>
      </article>
    </div>
  </div>
</template>

<script>
import { groq } from "@nuxtjs/sanity";
export default {
  async asyncData({ $sanity }) {
    const query = groq`*[_type == "post"]|order(publishedAt desc){title, publishedAt, slug, mainImage{asset->{_id, url}}, categories[]->{title, "id":_id}}`;
    const articles = await $sanity.fetch(query);
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

<style>
</style>
<template>
  <div class="py-5 px-6 container mx-auto">
    <h1>Sanity</h1>
    <div v-for="post in posts" :key="post._id">
      {{ post.title }} {{ formatDate(post.publishedAt) }}
      {{ post.mainImage.asset.url }}
      <div class="prose">
        <!-- <SanityContent :blocks="post.body" /> -->
      </div>
    </div>
    <img src="" alt="" />
  </div>
</template>

<script>
import { groq } from "@nuxtjs/sanity";
import { SanityContent } from "@nuxtjs/sanity/dist/components/sanity-content";

export default {
  async asyncData({ $sanity }) {
    const query = groq`*[_type == "post"]{title, publishedAt, mainImage{asset->{_id, url}}}`;
    const posts = await $sanity.fetch(query);
    return { posts };
  },
  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("id", options);
    },
  },
  components: {
    SanityContent,
  },
};
</script>

<style>
</style>
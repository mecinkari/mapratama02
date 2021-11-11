<template>
  <article class="prose prose-lg prose-blue mx-auto py-5">
    <nuxt-content :document="article" />
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content("blog", params.slug).fetch();

    return { article };
  },
  mounted() {
    let typo = document.createElement("link");
    typo.setAttribute("rel", "stylesheet");
    typo.setAttribute(
      "href",
      "https://cdn.jsdelivr.net/npm/@tailwindcss/typography@0.4.x/dist/typography.min.css"
    );
    document.head.appendChild(typo);
  },
};
</script>

<style>
</style>
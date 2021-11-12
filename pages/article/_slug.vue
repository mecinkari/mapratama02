<template>
  <div class="py-6">
    <article
      class="
        prose prose-sm
        md:prose
        lg:prose-lg
        prose-blue
        max-w-none
        shadow
        rounded
        mx-auto
        bg-white
        p-5
      "
    >
      <nuxt-content :document="article" />
    </article>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content("blog", params.slug)
      .where({ status: "published" })
      .fetch();

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

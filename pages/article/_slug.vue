<template>
  <div class="py-6">
    <div class="relative mb-12">
      <div
        class="
          absolute
          w-full
          h-full
          bg-black bg-opacity-50
          flex
          justify-center
          items-center
        "
      >
        <div class="text-center">
          <p class="text-3xl text-white">{{ article.title }}</p>
        </div>
      </div>
      <img
        v-if="article.img"
        :src="`/assets/blog/${article.img}`"
        class="h-96 object-cover w-full"
        alt=""
      />
      <img
        class="rounded-lg h-96 object-cover w-full"
        v-else
        src="https://via.placeholder.com/1024x768/eee?text=4:3"
      />
    </div>
    <article class="max-w-2xl shadow rounded mx-auto bg-white p-5">
      <nuxt-content
        class="prose prose-sm md:prose lg:prose-lg prose-blue"
        :document="article"
      />

      <prev-next :prev="prev" :next="next" />
    </article>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content("blog", params.slug)
      .where({ status: "published" })
      .fetch();

    const [prev, next] = await $content("blog")
      .only(["title", "slug"])
      .sortBy("createdAt", "asc")
      .surround(params.slug)
      .where({ status: "published" })
      .fetch();

    return { article, prev, next };
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

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
          <!-- <p class="text-white">Dibuat oleh: {{ article.author }}</p> -->
        </div>
      </div>
      <img
        v-if="article.mainImage.asset.url"
        :src="`${article.mainImage.asset.url}`"
        class="h-96 object-cover w-full"
        alt=""
      />
      <img
        class="rounded-lg h-96 object-cover w-full"
        v-else
        src="https://via.placeholder.com/1024x768/eee?text=4:3"
      />
    </div>
    <article
      class="max-w-2xl prose md:prose-lg shadow rounded mx-auto bg-white p-5"
    >
      <SanityContent :blocks="article.body" :serializers="serializers" />
      {{ serializers }}
    </article>
  </div>
</template>

<script>
import { groq } from "@nuxtjs/sanity";
export default {
  async asyncData({ params, $sanity }) {
    const query = groq`*[_type == "post" && slug.current == "${params.slug}"][0]{title, publishedAt, slug, mainImage{asset->{_id, url}}, body}`;
    const article = await $sanity.fetch(query);
    return { article };
  },
  // serializers() {
  //   const serializers = {
  //     types: {
  //       code: (props) => (
  //         <pre data-language={props.language}>
  //           <code>{props.code}</code>
  //         </pre>
  //       ),
  //     },
  //   };
  //   return { serializers };
  // },
  mounted() {
    let typo = document.createElement("link");
    typo.setAttribute("rel", "stylesheet");
    typo.setAttribute(
      "href",
      "https://cdn.jsdelivr.net/npm/@tailwindcss/typography@0.4.x/dist/typography.min.css"
    );
    document.head.appendChild(typo);
  },
  data() {
    return {
      serializers: {
        types: {
          code: (props) => {
            props.code;
          },
        },
      },
    };
  },
};
</script>

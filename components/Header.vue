<template>
  <header class="mb-12">
    <div class="text-center py-10">
      <p class="text-4xl font-black">Mapratama02</p>
      <p>Muhammad Anugrah Pratama</p>
    </div>
    <nav class="w-full p-4 bg-white flex gap-x-10 justify-center items-center">
      <nuxt-link
        v-for="link in links"
        :key="link.id"
        class="text-gray-600 font-bold"
        :to="link.to"
        >{{ link.title }}</nuxt-link
      >
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      myname: "Hola",
      links: [
        {
          id: 1,
          title: "Beranda",
          to: "/",
        },
        {
          id: 2,
          title: "Blog",
          to: "/blog",
        },
        // {
        //   id: 2,
        //   title: "Sanity",
        //   to: "/sanity",
        // },
        {
          id: 4,
          title: "About",
          to: "/about",
        },
      ],
    };
  },
};
</script>

<style>
</style>
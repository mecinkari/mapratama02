<template>
  <header
    class="w-full p-4 bg-white shadow flex gap-x-10 justify-center items-center"
  >
    <nuxt-link
      v-for="link in links"
      :key="link.id"
      class="text-gray-600 font-bold"
      :to="link.to"
      >{{ link.title }}</nuxt-link
    >
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
          title: "Home",
          to: "/",
        },
        {
          id: 2,
          title: "Blog",
          to: "/blog",
        },
        {
          id: 3,
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
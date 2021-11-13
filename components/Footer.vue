<template>
  <footer
    class="
      px-12
      py-3
      grid grid-cols-1
      gap-y-2
      md:gap-x-6 md:grid-cols-3
      mt-12
      border-t
    "
  >
    <div>
      <p class="text-2xl mb-2">Links</p>
      <hr class="border-b" />
      <div class="flex flex-col divide-y">
        <a
          class="block py-2"
          v-for="link in footerLinks"
          :key="link.id"
          :href="link.href"
          target="_blank"
          rel="noopener noreferrer"
          >{{ link.title }}</a
        >
      </div>
    </div>
    <!--  -->
    <div>
      <p class="text-2xl mb-2">Social Links</p>
      <hr class="border-b" />
      <div class="flex flex-col divide-y">
        <a
          class="block py-2"
          v-for="link in socialLinks"
          :key="link.id"
          :href="link.href"
          target="_blank"
          rel="noopener noreferrer"
          >{{ link.title }}</a
        >
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      footerLinks: [
        {
          id: 1,
          title: "Universitas Gunadarma",
          href: "http://www.gunadarma.ac.id/",
        },
        {
          id: 2,
          title: "V-Class Gunadarma",
          href: "https://v-class.gunadarma.ac.id/login/index.php",
        },
        {
          id: 3,
          title: "StudentSite Gunadarma",
          href: "https://studentsite.gunadarma.ac.id/index.php/site/index",
        },
        {
          id: 4,
          title: "BAAK Gunadarma",
          href: "http://baak.gunadarma.ac.id/",
        },
      ],
      socialLinks: [
        {
          id: 1,
          title: "Github",
          href: "https://github.com/mecinkari/",
        },
        {
          id: 2,
          title: "Twitter",
          href: "https://twitter.com/mecinkari",
        },
      ],
    };
  },
};
</script>

<style>
</style>
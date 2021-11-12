<template>
  <div class="py-5 max-w-2xl px-6 mx-auto">
    <div class="">
      <h1 class="text-4xl font-bold">Hello!</h1>
    </div>
    <hr class="border my-4" />
    <div class="prose prose-sm md:prose lg:prose-lg prose-blue mx-auto">
      <img
        src="~/static/assets/profile.jpg"
        class="w-40 rounded-full shadow"
        alt="profile"
      />
      <p>
        Nama saya "Muhammad Anugrah Pratama", tapi orang biasa panggil saya
        "Tama" atau "Anugrah". Saya kelahiran Jakarta, 18 Desember 2002. Saat
        ini saya seorang mahasiswa di Universitas Gunadarma.
      </p>
      <p>
        Saya punya interest dalam bidang <i>coding</i>. Saya telah belajar
        beberapa bahasa pemrograman beserta frameworknya seperti JavaScript,
        PHP, Dart, Java, Python, Vue, React, CSS, CodeIgniter, Laravel,
        Bootstrap, Bulma dan Tailwind CSS.
      </p>
      <p>
        Saya juga mempunyai hobi menggambar dan hobi ini saya gunakan sebagai
        pekerjaan <em>freelance</em>.
      </p>
      <hr />
      <p>
        Website ini dibuat oleh saya dari awal menggunakan
        <a href="http://vuejs.org" target="_blank">Vue.js</a>,
        <a href="http://nuxtjs.org" target="_blank">NuxtJS</a>
      </p>
    </div>
  </div>
</template>

<script>
export default {
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

<style scoped>
img {
  margin: 0 auto;
}
</style>

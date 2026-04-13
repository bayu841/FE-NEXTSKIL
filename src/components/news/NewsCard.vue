<script setup>
import GlareHover from "../GlareHover.vue";

// Dummy data berita
const newsList = [
  {
    id: 1,
    title: "Programming",
    desc: "Mulai perjalanan coding kamu dengan langkah yang tepat. Pelajari dasar-dasar penting agar tidak bingung di awal.",
    image: new URL("../../assets/images/news/newsimg.webp", import.meta.url).href,
  },
  {
    id: 2,
    title: "Belajar HTML",
    desc: "Pelajari dasar HTML untuk membangun website dari nol dengan mudah.",
    image: new URL("../../assets/images/news/newsimg.webp", import.meta.url).href,
  },
  {
    id: 3,
    title: "Belajar CSS",
    desc: "Buat tampilan website kamu lebih menarik dengan CSS modern.",
    image: new URL("../../assets/images/news/newsimg.webp", import.meta.url).href,
  },
  {
    id: 4,
    title: "Belajar JavaScript",
    desc: "Tambahkan interaksi ke website kamu dengan JavaScript.",
    image: new URL("../../assets/images/news/newsimg.webp", import.meta.url).href,
  },
  {
    id: 5,
    title: "Frontend Developer",
    desc: "Pelajari skill frontend untuk menjadi developer profesional.",
    image: new URL("../../assets/images/news/newsimg.webp", import.meta.url).href,
  },
  {
    id: 6,
    title: "Backend Developer",
    desc: "Bangun sistem backend yang kuat dan scalable.",
    image: new URL("../../assets/images/news/newsimg.webp", import.meta.url).href,
  },
];
</script>

<template>
  <h2 class="text-3xl font-semibold text-center text-gray-800 mb-4 font-poppins">
    Artikel Dan Berita Terbaru
  </h2>

  <section class="max-w-6xl mx-auto px-10 py-10 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
    
    <!-- LOOP DI SINI -->
    <GlareHover
      v-for="item in newsList"
      :key="item.id"
      class="w-full overflow-hidden transition-all duration-300 ease-out hover:-translate-y-1 hover:shadow-lg"
      background="#ffffff"
      border-color="#e5e7eb"
      border-radius="12px"
      glare-color="#93c5fd"
      :glare-opacity="0.25"
      :glare-size="250"
      :transition-duration="700"
    >

      <!-- IMAGE -->
      <div class="overflow-hidden rounded-t-xl">
        <img 
          :src="item.image" 
          class="w-full h-48 object-cover transition duration-500"
        >
      </div>

      <!-- CONTENT -->
      <div class="p-6 text-start">

        <h3 class="text-lg font-semibold mb-2 font-poppins">
          {{ item.title }}
        </h3>
        
        <p class="text-sm text-gray-500 leading-relaxed">
          {{ item.desc }}
        </p>

        <!-- BUTTON (FIX ERROR DI SINI) -->
        <router-link 
          :to="`/news/${item.id}`"
          class="inline-block mt-4 bg-gradient-to-r from-blue-600 to-indigo-600 text-white px-4 py-2 rounded-lg hover:to-blue-400 font-semibold"
        >
          Baca Artikel
        </router-link>

      </div>

    </GlareHover>

  </section>

  <!-- PATTERN -->
  <div class="flex justify-end px-10 mt-10">
    <img 
      src="../../assets/images/pattern3.webp" 
      class="w-[200px] opacity-60 rotate-[12deg] ml-10"
    />
  </div>
</template>
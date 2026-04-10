<template>
     <section class="pt-24 px-6">
  <div class="max-w-7xl mx-auto flex flex-col md:flex-row items-center gap-20">
    
    <!-- KIRI (TEXT) -->
    <div class="md:w-1/2 text-center md:text-left px-10">
      <h1 class="font-poppins text-4xl md:text-5xl font-bold leading-tight">
        Belajar Coding Lebih Mudah di 
        <span class="text-blue-600">NextSkill</span>
      </h1>

      <p class="mt-4 text-gray-600 text-lg">
        Tingkatkan skill kamu dengan materi berkualitas, mentor berpengalaman, dan pembelajaran yang fleksibel.
      </p>

      <div class="mt-6 flex justify-center md:justify-start gap-4">
        <button class="bg-gradient-to-r from-blue-600 to-indigo-600 
        text-white px-6 py-3 rounded-lg 
        hover:scale-105 transition">
          Mulai Belajar
        </button>

        <button class="border border-gray-300 px-6 py-3 rounded-lg hover:bg-gray-100">
          Lihat Kelas
        </button>
      </div>
    </div>

    <!-- KANAN (IMAGE) -->
    <div class="md:w-1/2">
      <img 
        src="/src/assets/images/hero.png" 
        alt="Hero Image"
        class="w-full max-w-md mx-auto py-3"
      />
    </div>

  </div>
</section>
</template>
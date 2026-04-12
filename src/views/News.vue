<script setup>
import AppLayout from "../layouts/AppLayout.vue";
import HeroSection from "../components/news/Hero.vue";
import NewsCard from "../components/news/NewsCard.vue";
import Footer from "../components/Footer.vue";
</script>

<template>
  <AppLayout>
    <HeroSection />
    <NewsCard />
    <Footer />
  </AppLayout>
</template>
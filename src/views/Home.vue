<script setup>
import HeroSection from "../components/HeroSection.vue";
import About from "../components/About.vue";
import AppLayout from "../layouts/AppLayout.vue";
import Class from "../components/Class.vue";
import Features from "../components/Features.vue";
import Benefit from "../components/Benefit.vue";
import Footer from "../components/Footer.vue";
import Testimoni from "../components/Testimoni.vue";
</script>

<template>
  <AppLayout>
    <HeroSection />
    <About />
    <Class />
    <Benefit />
    <Features />
    <Testimoni />
    <Footer />
  </AppLayout>
</template>
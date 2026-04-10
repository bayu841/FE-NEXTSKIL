<script setup lang="ts">
import { computed } from "vue";

const props = defineProps({
  text: String,
  color: { default: "#2563eb" },
  shineColor: { default: "#93c5fd" },
  className: { default: "" }
});

const style = computed(() => ({
  backgroundImage: `linear-gradient(120deg, ${props.color}, ${props.shineColor}, ${props.color})`,
  backgroundSize: "200% auto",
  WebkitBackgroundClip: "text",
  WebkitTextFillColor: "transparent",
  animation: "shine 2s linear infinite"
}));
</script>

<template>
  <span :class="className" :style="style">
    {{ text }}
  </span>
</template>

<style>
@keyframes shine {
  0% {
    background-position: 0% center;
  }
  100% {
    background-position: 200% center;
  }
}
</style>
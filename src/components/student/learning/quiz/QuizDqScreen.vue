<script setup>
import { ShieldAlert } from 'lucide-vue-next'

defineEmits(['restart'])
</script>

<template>
  <div class="flex flex-col items-center justify-center text-center p-8 md:p-12 bg-red-600 text-white min-h-[600px] rounded-3xl z-[100] relative">
    <div class="w-16 h-16 bg-white/20 rounded-2xl flex items-center justify-center mb-6 border-2 border-white animate-pulse">
        <ShieldAlert class="w-8 h-8" />
    </div>
    <h2 class="text-2xl md:text-3xl font-black mb-3 uppercase tracking-tight leading-none">DISKUALIFIKASI!</h2>
    <p class="text-red-100 max-w-sm font-medium text-sm md:text-base mb-8">Percobaan curang terdeteksi. Silakan ulangi dari awal.</p>
    <button @click="$emit('restart')" class="px-6 py-3 bg-white text-red-600 font-bold rounded-xl shadow-md active:scale-95 transition-all text-sm">
      ULANGI UJIAN
    </button>
  </div>
</template>

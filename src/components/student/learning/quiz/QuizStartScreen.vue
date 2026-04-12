<script setup>
import { ShieldAlert, Maximize2, AlertTriangle, ArrowRight } from 'lucide-vue-next'

defineEmits(['start'])
</script>

<template>
  <div class="flex flex-col items-center justify-center p-8 md:p-12 text-center min-h-[600px] bg-gradient-to-br from-indigo-50/50 to-white rounded-3xl">
    <div class="w-20 h-20 bg-indigo-600 rounded-3xl flex items-center justify-center text-white mb-6 shadow-xl shadow-indigo-100">
      <ShieldAlert class="w-10 h-10" />
    </div>
    <h2 class="text-2xl font-bold text-gray-900 mb-2 tracking-tight">Security Access</h2>
    <p class="text-gray-500 font-medium text-sm mb-8 max-w-sm">Klik tombol di bawah untuk masuk ke mode ujian aman (Layar Penuh).</p>
    <div class="max-w-sm w-full space-y-3 mb-10 text-left">
      <div class="bg-white p-3 rounded-lg border border-gray-100 flex gap-2 shadow-sm border-l-4 border-l-indigo-500">
        <Maximize2 class="w-4 h-4 text-indigo-500 shrink-0 mt-0.5" />
        <p class="text-xs font-bold text-gray-700">Wajib Mode Fullscreen. Keluar dari fullscreen = Gagal.</p>
      </div>
      <div class="bg-white p-3 rounded-lg border border-gray-100 flex gap-2 shadow-sm border-l-4 border-l-red-500">
        <AlertTriangle class="w-4 h-4 text-red-500 shrink-0 mt-0.5" />
        <p class="text-xs font-bold text-gray-700">Dilarang pindah tab browser atau buka aplikasi lain.</p>
      </div>
    </div>
    <button @click="$emit('start')" class="px-6 py-3 bg-indigo-600 text-white font-bold text-sm rounded-xl shadow-md flex items-center gap-2 hover:bg-indigo-700 active:scale-95 transition-all">
      MASUK UJIAN
      <ArrowRight class="w-4 h-4" />
    </button>
  </div>
</template>

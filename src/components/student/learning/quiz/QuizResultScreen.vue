<script setup>
import { Trophy, RotateCcw } from 'lucide-vue-next'

defineProps({
  isRemedial: {
    type: Boolean,
    required: true
  },
  finalScorePercentage: {
    type: Number,
    required: true
  }
})

defineEmits(['restart', 'finish'])
</script>

<template>
  <div class="flex flex-col items-center justify-center p-8 md:p-12 text-center min-h-[600px] bg-white rounded-3xl">
    <div class="w-20 h-20 bg-indigo-600 rounded-2xl flex items-center justify-center text-white mb-6 shadow-md shadow-indigo-200">
      <Trophy class="w-10 h-10" />
    </div>
    <h2 class="text-3xl md:text-4xl font-black mb-2 tracking-tight text-gray-900 leading-none">{{ isRemedial ? 'COBA LAGI!' : 'LULUS!' }}</h2>
    <p class="text-gray-400 font-bold text-xs md:text-sm uppercase tracking-widest mb-8">{{ isRemedial ? 'PELAJARI MATERI KEMBALI' : 'KAMU MEMANG HEBAT!' }}</p>
    
    <div class="w-full max-w-xs bg-gray-50 rounded-3xl p-8 mb-10 border border-gray-100 shadow-sm flex flex-col items-center">
      <span class="text-5xl md:text-6xl font-black text-indigo-600 tracking-tighter leading-none">{{ finalScorePercentage }}</span>
      <span class="text-xs font-bold text-gray-400 mt-2 tracking-widest text-center block">SKOR AKHIR</span>
    </div>

    <div class="flex gap-4 w-full max-w-sm pb-10">
        <button @click="$emit('restart')" v-if="!isRemedial" class="flex-1 px-6 py-3 bg-white border border-gray-200 text-gray-600 font-bold rounded-xl hover:bg-gray-50 flex items-center justify-center gap-2 text-sm transition-colors">
          <RotateCcw class="w-4 h-4" /> ULANGI
        </button>
        <button @click="$emit('finish')" class="flex-1 px-6 py-3 text-white font-bold text-sm rounded-xl shadow-md transition-all active:scale-95"
          :class="isRemedial ? 'bg-red-600 shadow-red-200 hover:bg-red-700' : 'bg-indigo-600 shadow-indigo-200 hover:bg-indigo-700'">
          {{ isRemedial ? 'Mulai Remidi' : 'Lanjutkan' }}
        </button>
    </div>
  </div>
</template>

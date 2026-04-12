<script setup>
import { CheckCircle2 } from 'lucide-vue-next'

const props = defineProps({
  question: {
    type: Object,
    required: true
  }
})

const selectCorrect = (idx) => {
  props.question.correctIndex = idx
}
</script>

<template>
  <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
    <div v-for="(_, oIdx) in question.options" :key="oIdx" class="relative group/option flex items-center">
      <div 
        class="w-10 h-10 shrink-0 rounded-lg flex items-center justify-center font-bold text-sm mr-3 transition-colors"
        :class="question.correctIndex === oIdx ? 'bg-emerald-500 text-white' : 'bg-gray-100 text-gray-500 border border-gray-200'"
      >
        {{ String.fromCharCode(65 + oIdx) }}
      </div>
      <input 
        v-model="question.options[oIdx]"
        class="w-full px-4 py-2.5 bg-white border rounded-xl focus:ring-2 focus:ring-indigo-500/20 focus:border-indigo-500 outline-none transition-all text-sm font-medium text-gray-700"
        :class="question.correctIndex === oIdx ? 'border-emerald-300' : 'border-gray-200'"
        :placeholder="'Jawaban ' + String.fromCharCode(65 + oIdx)"
      />
      <div class="absolute right-3 translate-y-1/2 bottom-1/2 flex items-center justify-center">
        <button 
            @click="selectCorrect(oIdx)"
            title="Tandai Sebagai Jawaban Benar"
            class="p-1.5 rounded-lg transition-colors bg-white"
            :class="question.correctIndex === oIdx ? 'text-emerald-500' : 'text-gray-300 hover:text-emerald-500'"
        >
            <CheckCircle2 class="w-5 h-5" />
        </button>
      </div>
    </div>
  </div>
</template>

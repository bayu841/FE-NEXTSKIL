<script setup>
import { Plus, Trash2, Layout } from 'lucide-vue-next'

const props = defineProps({
  question: {
    type: Object,
    required: true
  }
})

const addMatchingItem = () => {
  const newId = props.question.leftItems.length + 1
  props.question.leftItems.push({ id: 'l' + newId, text: '' })
  props.question.rightItems.push({ id: 'r' + newId, text: '' })
  props.question.pairs['l' + newId] = 'r' + newId
}

const removePair = (iIdx) => {
  const leftId = props.question.leftItems[iIdx].id
  props.question.leftItems.splice(iIdx, 1)
  props.question.rightItems.splice(iIdx, 1)
  delete props.question.pairs[leftId]
}
</script>

<template>
  <div class="space-y-4">
    <div v-for="(item, iIdx) in question.leftItems" :key="iIdx" class="flex gap-3 items-center">
      <div class="flex-1">
        <label class="block text-xs font-bold text-gray-500 mb-1" v-if="iIdx === 0">Premis (Kiri)</label>
        <input 
          v-model="question.leftItems[iIdx].text"
          class="w-full px-3 py-2.5 bg-white border border-gray-200 rounded-lg focus:border-indigo-500 outline-none transition-all text-sm"
          placeholder="Contoh: HTML"
        />
      </div>
      <div class="text-gray-400 flex items-center justify-center mt-5">
        <Layout class="w-4 h-4" />
      </div>
      <div class="flex-1 pb-0 relative">
        <label class="block text-xs font-bold text-emerald-600 mb-1" v-if="iIdx === 0">Pasangan (Kanan)</label>
        <input 
          v-model="question.rightItems[iIdx].text"
          class="w-full px-3 py-2.5 bg-emerald-50 border border-emerald-200 rounded-lg focus:border-emerald-500 outline-none transition-all text-sm text-emerald-800"
          placeholder="Contoh: Struktur Web"
        />
        <button @click="removePair(iIdx)" class="absolute -right-8 top-1/2 mt-2.5 -translate-y-1/2 text-gray-400 hover:text-red-500 transition-colors">
            <Trash2 class="w-4 h-4" />
        </button>
      </div>
    </div>
    <!-- ADD PAIR -->
    <button 
      @click="addMatchingItem"
      class="w-full py-3 border-2 border-dashed border-gray-200 mt-2 rounded-xl text-gray-500 hover:border-indigo-300 hover:text-indigo-600 hover:bg-gray-50 transition-colors font-medium text-sm flex items-center justify-center gap-2"
    >
      <Plus class="w-4 h-4" />
      Tambah Pasangan
    </button>
  </div>
</template>

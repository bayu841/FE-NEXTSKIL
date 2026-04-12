<script setup>
import { ref } from 'vue'
import { Upload, FileText, X } from 'lucide-vue-next'

const props = defineProps({
  modelValue: {
    type: File,
    default: null
  }
})

const emit = defineEmits(['update:modelValue'])

const isDragging = ref(false)

const handleFileUpload = (event) => {
  const f = event.target.files[0]
  if (f) emit('update:modelValue', f)
}

const removeFile = () => {
  emit('update:modelValue', null)
}
</script>

<template>
  <div class="space-y-2">
    <label class="block text-sm font-bold text-gray-800 ml-1">Lampiran Pendukung (Opsional)</label>
    <div 
      @dragover.prevent="isDragging = true"
      @dragleave.prevent="isDragging = false"
      @drop.prevent="isDragging = false; handleFileUpload($event)"
      class="relative border-2 border-dashed rounded-2xl p-8 transition-all group flex flex-col items-center justify-center text-center gap-3"
      :class="[
        isDragging ? 'border-indigo-500 bg-indigo-50/50' : 'border-gray-200 hover:border-indigo-300 hover:bg-gray-50',
        modelValue ? 'bg-emerald-50/30 border-emerald-300' : ''
      ]"
    >
      <input 
        type="file" 
        @change="handleFileUpload"
        class="absolute inset-0 w-full h-full opacity-0 cursor-pointer"
      />
      
      <div v-if="!modelValue" class="space-y-2 pointer-events-none">
        <div class="w-10 h-10 bg-gray-50 border border-gray-100 rounded-lg flex items-center justify-center mx-auto text-gray-400 shadow-sm group-hover:text-indigo-600 group-hover:border-indigo-100 transition-all duration-300">
          <Upload class="w-5 h-5" />
        </div>
        <div>
          <p class="text-gray-800 text-sm font-medium">Seret file zip, pdf, atau pptx kesini</p>
          <p class="text-xs text-gray-400 mt-1">Maksimal 100MB</p>
        </div>
      </div>

      <div v-else class="w-full z-10 relative">
        <div class="flex items-center gap-3 bg-white p-3 rounded-xl border border-emerald-100 shadow-sm max-w-sm mx-auto relative group/file">
          <div class="w-10 h-10 bg-emerald-500 rounded-lg flex items-center justify-center text-white shrink-0">
            <FileText class="w-5 h-5" />
          </div>
          <div class="text-left overflow-hidden">
            <p class="text-sm font-bold text-gray-900 truncate">{{ modelValue.name }}</p>
            <p class="text-xs text-gray-500 mt-0.5">{{ (modelValue.size / (1024 * 1024)).toFixed(2) }} MB</p>
          </div>
          <button 
            @click.stop="removeFile"
            class="absolute -top-2 -right-2 w-6 h-6 bg-red-500 text-white rounded-full flex items-center justify-center shadow-md hover:bg-red-600 transition-all scale-90 hover:scale-100"
          >
            <X class="w-3 h-3" />
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { ArrowLeft, CheckCircle2 } from 'lucide-vue-next'
import BaseModal from '../../../components/shared/BaseModal.vue'
import FileDropzone from '../../../components/mentor/courses/material/FileDropzone.vue'

const router = useRouter()
const route = useRoute()
const courseId = route.params.courseId || '1' // Fallback dummy

const form = ref({
  title: '',
  description: '',
  file: null
})

const modalState = ref({
  isOpen: false,
  title: '',
  message: '',
  type: 'info'
})

const handleSubmit = () => {
  if (!form.value.title || (!form.value.file && !form.value.description)) {
    showModal('Oops!', 'Mohon isi judul dan penuhi isi materi ATAU upload lampiran file.', 'warning')
    return
  }
  showModal('Berhasil!', 'Materi kursus telah berhasil dipublikasikan.', 'success')
}

const showModal = (title, message, type = 'info') => {
  modalState.value = {
    isOpen: true,
    title,
    message,
    type
  }
}

const closeModal = () => {
  modalState.value.isOpen = false
}

const handleModalConfirm = () => {
  closeModal()
  if (modalState.value.title === 'Berhasil!') {
    router.push('/mentor/courses')
  }
}
</script>

<template>
  <div class="max-w-4xl mx-auto space-y-6 animate-in fade-in slide-in-from-bottom-4 duration-500">
    <!-- Header -->
    <div class="flex flex-col gap-2 border-b border-gray-100 pb-6">
      <button 
        @click="router.back()" 
        class="flex items-center gap-2 text-sm text-gray-500 hover:text-indigo-600 transition-colors w-fit group"
      >
        <ArrowLeft class="w-4 h-4 group-hover:-translate-x-1 transition-transform" />
        Kembali ke Daftar Kursus
      </button>
      <div>
        <h1 class="text-2xl font-bold text-gray-900 tracking-tight">Buat Materi Baru</h1>
        <p class="text-gray-500 mt-1 text-sm font-medium">Buat materi pembelajaran baru untuk kursus ini.</p>
      </div>
    </div>

    <!-- MAIN FORM CONTAINER -->
    <div class="bg-white rounded-2xl border border-gray-100 shadow-sm p-6 space-y-6">
      
      <!-- Title -->
      <div class="space-y-2">
        <label class="block text-sm font-bold text-gray-800 ml-1">Judul Materi Pembelajaran</label>
        <input 
          v-model="form.title"
          type="text" 
          placeholder="Masukkan judul materi..."
          class="w-full px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl focus:ring-2 focus:ring-indigo-500/20 focus:border-indigo-500 transition-all outline-none text-sm text-gray-900 placeholder:text-gray-400"
        />
      </div>

      <!-- Description -->
      <div class="space-y-2">
        <label class="flex justify-between items-center ml-1">
            <span class="text-sm font-bold text-gray-800">Isi Konten Materi</span>
            <span class="text-[10px] font-medium text-gray-500 bg-gray-100 px-2 py-1 rounded">Markdown Supported</span>
        </label>
        <textarea 
          v-model="form.description"
          rows="8" 
          placeholder="Tuliskan isi materi di sini..."
          class="w-full px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl focus:ring-2 focus:ring-indigo-500/20 focus:border-indigo-500 transition-all outline-none text-sm text-gray-700 leading-relaxed custom-scrollbar placeholder:text-gray-400"
        ></textarea>
      </div>

      <div class="relative flex items-center py-2">
          <div class="flex-grow border-t border-gray-100"></div>
          <span class="flex-shrink-0 mx-4 text-gray-400 text-xs font-medium">Atau / Dan Sertakan File</span>
          <div class="flex-grow border-t border-gray-100"></div>
      </div>

      <!-- File Upload extracted Component -->
      <FileDropzone v-model="form.file" />

      <!-- Submit Button -->
      <div class="pt-4 border-t border-gray-100">
        <button 
          @click="handleSubmit"
          class="w-full py-3 bg-gray-900 hover:bg-indigo-600 text-white font-bold rounded-xl shadow-md transition-all active:scale-[0.98] flex items-center justify-center gap-2 text-sm"
        >
          <CheckCircle2 class="w-4 h-4" />
          TERBITKAN MATERI
        </button>
      </div>
    </div>

    <!-- Feedback Modal -->
    <BaseModal
      :is-open="modalState.isOpen"
      :title="modalState.title"
      :message="modalState.message"
      :type="modalState.type"
      confirm-text="Paham"
      @confirm="handleModalConfirm"
      @close="closeModal"
    />
  </div>
</template>

<style scoped>
.custom-scrollbar::-webkit-scrollbar { width: 6px; }
.custom-scrollbar::-webkit-scrollbar-track { background: transparent; }
.custom-scrollbar::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 10px; }
.custom-scrollbar::-webkit-scrollbar-thumb:hover { background: #94a3b8; }
</style>

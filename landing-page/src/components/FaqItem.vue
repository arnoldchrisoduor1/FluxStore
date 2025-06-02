<template>
  
  <div class="shadow shadow-indigo-300 py-4 px-2 mt-5 rounded-md">
    <button
      @click="isOpen = !isOpen"
      class="w-full flex justify-between items-center text-left"
    >
      <span class="text-indigo-600 font-semibold">
        {{ question }}
      </span>
      <ChevronDown
        :class="['w-5 h-5 transition-transform duration-300', { 'rotate-180': isOpen }]"
        class="text-indigo-500"
      />
    </button>
    <div
      v-if="isOpen"
      class="mt-2 text-gray-700 transition-opacity duration-300"
    >
      {{ answer }}
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { ChevronDown } from 'lucide-vue-next'

const props = defineProps({
  question: String,
  answer: String,
})

const isOpen = ref(false)
</script>

<style scoped>
/* You can add any extra styles here if needed */
</style>

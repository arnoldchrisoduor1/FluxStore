<template>
  <Transition name="fadein">
    <div class="shadow-lg shadow-indigo-200/50 py-4 px-4 mt-3 rounded-lg bg-gradient-to-b from-indigo-50/30 to-white hover:cursor-pointer">
      <button
        @click="isOpen = !isOpen"
        class="w-full flex justify-between items-center text-left group"
      >
        <span class="text-indigo-800 font-semibold text-lg group-hover:text-violet-700 transition-colors duration-200 hover:cursor-pointer">
          {{ question }}
        </span>
        <ChevronDown
          :class="['w-6 h-6 transition-all duration-300', { 'rotate-180 text-violet-600': isOpen }]"
          class="text-indigo-500 group-hover:text-violet-600"
        />
      </button>
      <Transition
        name="fadeinlag"
        appear
      >
        <div
          v-if="isOpen"
          class="mt-4 text-indigo-900/90 pl-1 pr-4 pb-2 transition-opacity duration-300"
        >
          {{ answer }}
        </div>
      </Transition>
    </div>
  </Transition>
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
.fadeinlag-enter-active {
  transition: all 0.5s ease 0.2s;
}
.fadeinlag-leave-active {
  transition: all 0.3s ease;
}
.fadeinlag-enter-from,
.fadeinlag-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

.fadein-enter-active {
  transition: all 0.5s ease;
}
.fadein-leave-active {
  transition: all 0.3s ease;
}
.fadein-enter-from,
.fadein-leave-to {
  opacity: 0;
  transform: translateY(20px);
}
</style>
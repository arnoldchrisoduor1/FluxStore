<template>
  <div class="flex flex-row gap-6 border border-indigo-200 rounded-xl min-w-full p-6 shadow-lg shadow-indigo-100/50 hover:shadow-xl hover:shadow-indigo-200/50 transition-all duration-300 items-center bg-white">
    <div class="bg-indigo-100/40 p-3 rounded-lg">
      <component :is="icon" class="h-7 w-7 text-indigo-700" />
    </div>
    <div>
      <p class="text-2xl font-bold text-indigo-800 mb-1">{{ value }}</p>
      <p class="text-sm text-indigo-600/90 font-medium tracking-wide">{{ title }}</p>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  title: String,
  value: String,
  icon: Object
})
</script>
<template>
    <div class="flex flex-row gap-10 border border-indigo-300 rounded-md min-w-[300px] p-3 mb-5 shadow shadow-indigo-400/30 items-center">
            <div>
                <component :is="icon" class="h-8 w-8 text-indigo-700" />
            </div>
            <div>
                <p class="text-xl font-bold text-indigo-600">{{ value }}</p>
                <p class="text-sm text-indigo-800 tracking-tight">{{ title }}</p>
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

<style></style>
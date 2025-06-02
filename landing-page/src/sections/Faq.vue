<template>
    <div class="text-center flex flex-col justify-center items-center gap-5">
            <div
                class="border border-indigo-100 px-2 rounded-full bg-gradient-to-r from-indigo-100/50 to-indigo-200/50">
                <p class="text-indigo-700">FAQs</p>
            </div>
            <h2 class="text-3xl text-indigo-800">Have Any Questions ?</h2>
        </div>
  <div class="w-[95%] mx-auto p-4">
    <FaqItem
      question="What is your return policy?"
      answer="You can return any item within 30 days for a full refund."
    />
    <FaqItem
      question="Do you offer international shipping?"
      answer="Yes, we ship to most countries worldwide."
    />
    <FaqItem
      question="How can I track my order?"
      answer="Once your order ships, we'll send you a tracking number by email."
    />
  </div>
</template>

<script setup>
import FaqItem from '../components/FaqItem.vue'
</script>

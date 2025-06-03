<template>
  <div class="text-center flex flex-col justify-center items-center gap-5 mb-10">
    <Transition name="sidefadein" appear>
      <div class="border border-violet-200 px-4 py-1 rounded-full bg-gradient-to-r from-violet-100/70 to-indigo-100/70 shadow-sm shadow-violet-100">
        <p class="text-violet-700 font-medium">FAQs</p>
      </div>
    </Transition>
    <Transition name="fadein" appear>
      <h2 class="text-4xl font-bold text-indigo-900 bg-gradient-to-r from-violet-600 to-indigo-600 bg-clip-text text-transparent">
        Have Any Questions?
      </h2>
    </Transition>
  </div>
  <div class="w-[90%] md:w-[80%] lg:w-[70%] mx-auto p-4 space-y-4">
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

<style>
/* Global transition styles */
.sidefadein-enter-active {
  transition: all 0.8s ease 0.1s;
}
.sidefadein-leave-active {
  transition: all 0.3s ease;
}
.sidefadein-enter-from {
  opacity: 0;
  transform: translateX(-50px);
}
.sidefadein-leave-to {
  opacity: 0;
  transform: translateX(50px);
}

.fadein-enter-active {
  transition: all 0.8s ease 0.3s;
}
.fadein-leave-active {
  transition: all 0.3s ease;
}
.fadein-enter-from {
  opacity: 0;
  transform: translateY(30px);
}
.fadein-leave-to {
  opacity: 0;
  transform: translateY(-30px);
}
</style>
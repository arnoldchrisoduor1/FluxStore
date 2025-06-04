<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import FaqItem from '../components/FaqItem.vue';

// Refs for each element
const faqTaglineRef = ref(null);
const faqHeadlineRef = ref(null);
const faqItemsRefs = ref([]);

// Visibility states
const faqTaglineVisible = ref(false);
const faqHeadlineVisible = ref(false);
const faqItemsVisible = ref([]);

// Initialize with false for each FAQ item
onMounted(() => {
  faqItemsVisible.value = Array(3).fill(false);
});

// Intersection Observer instance
let observer = null;

const createObserver = () => {
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          if (entry.target === faqTaglineRef.value) faqTaglineVisible.value = true;
          else if (entry.target === faqHeadlineRef.value) faqHeadlineVisible.value = true;
          else if (faqItemsRefs.value.includes(entry.target)) {
            const index = faqItemsRefs.value.indexOf(entry.target);
            faqItemsVisible.value[index] = true;
          }
        } else {
          // Optional: Reset visibility when element leaves viewport
          if (entry.target === faqTaglineRef.value) faqTaglineVisible.value = false;
          else if (entry.target === faqHeadlineRef.value) faqHeadlineVisible.value = false;
          else if (faqItemsRefs.value.includes(entry.target)) {
            const index = faqItemsRefs.value.indexOf(entry.target);
            faqItemsVisible.value[index] = false;
          }
        }
      });
    },
    {
      threshold: 0.1,
      rootMargin: '50px'
    }
  );
};

onMounted(() => {
  createObserver();
  
  // Observe all elements
  const elements = [
    faqTaglineRef.value,
    faqHeadlineRef.value,
    ...faqItemsRefs.value
  ].filter(el => el);
  
  elements.forEach(el => observer.observe(el));
});

onUnmounted(() => {
  if (observer) {
    observer.disconnect();
  }
});

// Function to set FAQ item ref
const setFaqItemRef = (el, index) => {
  if (el) {
    faqItemsRefs.value[index] = el;
  }
};
</script>

<template>
  <div>
    <div class="text-center flex flex-col justify-center items-center gap-5 mb-10">
      <div 
        ref="faqTaglineRef"
        :class="[
          'border border-violet-200 px-4 py-1 rounded-full bg-gradient-to-r from-violet-100/70 to-indigo-100/70 shadow-sm shadow-violet-100',
          'transition-all duration-1000 ease-out',
          faqTaglineVisible ? 'opacity-100 translate-x-0' : 'opacity-0 -translate-x-12'
        ]"
      >
        <p class="text-violet-700 font-medium">FAQs</p>
      </div>
      
      <h2 
        ref="faqHeadlineRef"
        :class="[
          'text-4xl font-bold text-indigo-900 bg-gradient-to-r from-violet-600 to-indigo-600 bg-clip-text text-transparent',
          'transition-all duration-1000 ease-out delay-200',
          faqHeadlineVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
        ]"
      >
        Have Any Questions?
      </h2>
    </div>
    
    <div class="w-[90%] md:w-[80%] lg:w-[70%] mx-auto p-4 space-y-4">
      <div 
        :ref="el => setFaqItemRef(el, 0)"
        :class="[
          'transition-all duration-700 ease-out',
          faqItemsVisible[0] ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
        ]"
        style="transition-delay: 100ms"
      >
        <FaqItem 
          question="What is your return policy?"
          answer="You can return any item within 30 days for a full refund." 
        />
      </div>
      
      <div 
        :ref="el => setFaqItemRef(el, 1)"
        :class="[
          'transition-all duration-700 ease-out',
          faqItemsVisible[1] ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
        ]"
        style="transition-delay: 200ms"
      >
        <FaqItem 
          question="Do you offer international shipping?" 
          answer="Yes, we ship to most countries worldwide." 
        />
      </div>
      
      <div 
        :ref="el => setFaqItemRef(el, 2)"
        :class="[
          'transition-all duration-700 ease-out',
          faqItemsVisible[2] ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
        ]"
        style="transition-delay: 300ms"
      >
        <FaqItem 
          question="How can I track my order?"
          answer="Once your order ships, we'll send you a tracking number by email." 
        />
      </div>
    </div>
  </div>
</template>

<style>
/* You can keep your existing styles if needed for other components */
</style>
<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import { Truck, ShieldPlus, Fingerprint, ReceiptEuro } from 'lucide-vue-next';

// Individual refs for each animated element
const taglineRef = ref(null);
const headlineRef = ref(null);
const subheadlineRef = ref(null);
const ctaRef = ref(null);
const trustBadgesRef = ref(null);
const orbRef = ref(null);

// Visibility states for each element
const taglineVisible = ref(false);
const headlineVisible = ref(false);
const subheadlineVisible = ref(false);
const ctaVisible = ref(false);
const trustBadgesVisible = ref(false);
const orbVisible = ref(false);

// Intersection Observer instance
let observer = null;

// Create intersection observer
const createObserver = () => {
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          // Map element to its visibility state
          if (entry.target === taglineRef.value) taglineVisible.value = true;
          else if (entry.target === headlineRef.value) headlineVisible.value = true;
          else if (entry.target === subheadlineRef.value) subheadlineVisible.value = true;
          else if (entry.target === ctaRef.value) ctaVisible.value = true;
          else if (entry.target === trustBadgesRef.value) trustBadgesVisible.value = true;
          else if (entry.target === orbRef.value) orbVisible.value = true;
        } else {
          // Optional: Reset visibility when element leaves viewport
          // Remove these if you want animations to only trigger once
          if (entry.target === taglineRef.value) taglineVisible.value = false;
          else if (entry.target === headlineRef.value) headlineVisible.value = false;
          else if (entry.target === subheadlineRef.value) subheadlineVisible.value = false;
          else if (entry.target === ctaRef.value) ctaVisible.value = false;
          else if (entry.target === trustBadgesRef.value) trustBadgesVisible.value = false;
          else if (entry.target === orbRef.value) orbVisible.value = false;
        }
      });
    },
    {
      threshold: 0.1, // Trigger when 10% of element is visible
      rootMargin: '50px' // Start animation 50px before element enters viewport
    }
  );
};

onMounted(() => {
  createObserver();
  
  // Observe all elements
  const elements = [
    taglineRef.value,
    headlineRef.value,
    subheadlineRef.value,
    ctaRef.value,
    trustBadgesRef.value,
    orbRef.value
  ];
  
  elements.forEach(el => {
    if (el) observer.observe(el);
  });
});

onUnmounted(() => {
  if (observer) {
    observer.disconnect();
  }
});
</script>

<template>
  <section id="home">
  <!-- Background Gradient -->
  <div class="bg-gradient-to-b from-white via-indigo-50 to-white h-[800px] md:h-[700px] absolute -z-20"></div>

  <!-- Hero Content -->
  <div class="relative max-w-7xl mx-auto px-6 lg:px-8 pt-24 md:pt-32 pb-20">
    <div class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
      <!-- Left Column: Text + CTA -->
      <div class="text-center md:text-left">
        <!-- Tagline -->
        <div 
          ref="taglineRef"
          :class="[
            'inline-flex items-center gap-2 bg-indigo-100/80 px-4 py-2 rounded-full mb-6 transition-all duration-1000 ease-out',
            taglineVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
          ]"
        >
          <span class="text-indigo-700 font-semibold">🚀 FluxStore</span>
          <span class="text-indigo-500">| Ecommerce Simplified</span>
        </div>

        <!-- Headline -->
        <h1 
          ref="headlineRef"
          :class="[
            'text-4xl md:text-5xl lg:text-6xl font-bold leading-tight mb-6 transition-all duration-1000 ease-out delay-200',
            headlineVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
          ]"
        >
          <span class="bg-gradient-to-r from-indigo-600 to-violet-700 text-transparent bg-clip-text">
            Sell Smarter, Buy Easier
          </span>
        </h1>

        <!-- Subheadline -->
        <p 
          ref="subheadlineRef"
          :class="[
            'text-lg md:text-xl text-indigo-800/90 mb-8 max-w-lg mx-auto md:mx-0 transition-all duration-1000 ease-out delay-400',
            subheadlineVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
          ]"
        >
          The all-in-one platform for sellers to grow their business and buyers to shop securely.
        </p>

        <!-- CTAs -->
        <div 
          ref="ctaRef"
          :class="[
            'flex flex-col sm:flex-row gap-4 justify-center md:justify-start mb-12 transition-all duration-1000 ease-out delay-500',
            ctaVisible ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-8'
          ]"
        >
          <button
            class="px-6 py-3.5 bg-gradient-to-r from-indigo-600 to-violet-600 text-white font-bold rounded-lg shadow-lg hover:shadow-xl transition-all hover:scale-[1.02] hover:cursor-pointer">
            Start Selling Free
          </button>
          <button
            class="px-6 py-3.5 bg-white border-2 border-indigo-200 text-indigo-700 font-bold rounded-lg hover:bg-indigo-50 transition-colors hover:cursor-pointer">
            Explore Shops
          </button>
        </div>

        <!-- Trust Badges -->
        <div 
          ref="trustBadgesRef"
          :class="[
            'flex flex-wrap justify-center md:justify-start items-center gap-4 text-sm text-indigo-600 transition-all duration-1000 ease-out delay-700',
            trustBadgesVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
          ]"
        >
          <div class="flex items-center gap-2">
            <Fingerprint class="w-4 h-4 text-violet-600" />
            <span>Secure Payments</span>
          </div>
          <div class="flex items-center gap-2">
            <Truck class="w-4 h-4 text-violet-600" />
            <span>Fast Delivery</span>
          </div>
        </div>
      </div>

      <!-- Right Column: Spinning Orb -->
      <div 
        ref="orbRef"
        :class="[
          'relative w-full h-[400px] md:h-[500px] flex justify-center items-center transition-all duration-1200 ease-out delay-300',
          orbVisible ? 'opacity-100 translate-x-0 scale-100' : 'opacity-0 translate-x-12 scale-95'
        ]"
      >
        <div
          class="w-[350px] h-[350px] md:w-[450px] md:h-[450px] rounded-full bg-white shadow-[inset_0_0_30px_theme('colors.indigo.200')] rotate-slow">
          <!-- Orb Items -->
          <div
            class="absolute top-[20px] left-[125px] md:left-[175px] w-[120px] h-[120px] rounded-full bg-white shadow-[inset_0_0_20px_theme('colors.indigo.300')] flex items-center justify-center">
            <div class="spin-counter text-center">
              <Truck class="h-10 w-10 mx-auto text-indigo-600" />
              <p class="font-medium mt-2 text-indigo-700 text-sm tracking-tighter">Fast Deliveries</p>
            </div>
          </div>
          <div
            class="absolute top-[120px] left-[20px] w-[120px] h-[120px] rounded-full bg-white shadow-[inset_0_0_20px_theme('colors.indigo.300')] flex items-center justify-center">
            <div class="spin-counter text-center">
              <ShieldPlus class="h-10 w-10 mx-auto text-indigo-600" />
              <p class="font-medium mt-2 text-indigo-700 text-sm tracking-tighter">Buyer Protection</p>
            </div>
          </div>
          <div
            class="absolute top-[230px] left-[125px] md:left-[175px] w-[120px] h-[120px] rounded-full bg-white shadow-[inset_0_0_20px_theme('colors.indigo.300')] flex items-center justify-center">
            <div class="spin-counter text-center">
              <Fingerprint class="h-10 w-10 mx-auto text-indigo-600" />
              <p class="font-medium mt-2 text-indigo-700 text-sm tracking-tighter">Secure Payments</p>
            </div>
          </div>
          <div
            class="absolute top-[120px] right-[20px] w-[120px] h-[120px] rounded-full bg-white shadow-[inset_0_0_20px_theme('colors.indigo.300')] flex items-center justify-center">
            <div class="spin-counter text-center">
              <ReceiptEuro class="h-10 w-10 mx-auto text-indigo-600" />
              <p class="font-medium mt-2 text-indigo-700 text-sm tracking-tighter">Easy Invoicing</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  </section>
</template>

<style>
@keyframes spin-reverse {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(-360deg);
  }
}

.rotate-slow {
  animation: spin-reverse 50s linear infinite;
}

@keyframes spin-forward {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.spin-counter {
  animation: spin-forward 50s linear infinite;
}
</style>
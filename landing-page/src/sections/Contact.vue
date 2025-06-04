<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import { ArrowRight, Rocket, Zap, BadgeCheck } from 'lucide-vue-next';

const features = [
  {
    icon: Rocket,
    text: "Launch your store in minutes"
  },
  {
    icon: Zap,
    text: "Powerful e-commerce tools"
  },
  {
    icon: BadgeCheck,
    text: "Trusted by 10,000+ sellers"
  }
];

// Refs for each element
const ctaContainerRef = ref(null);
const headlineRef = ref(null);
const subheadlineRef = ref(null);
const featuresRef = ref(null);
const ctaButtonRef = ref(null);
const trustIndicatorsRef = ref(null);
const userAvatarsRef = ref(null);

// Visibility states
const ctaContainerVisible = ref(false);
const headlineVisible = ref(false);
const subheadlineVisible = ref(false);
const featuresVisible = ref(false);
const ctaButtonVisible = ref(false);
const trustIndicatorsVisible = ref(false);
const userAvatarsVisible = ref(false);

// Intersection Observer instance
let observer = null;

const createObserver = () => {
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          if (entry.target === ctaContainerRef.value) ctaContainerVisible.value = true;
          else if (entry.target === headlineRef.value) headlineVisible.value = true;
          else if (entry.target === subheadlineRef.value) subheadlineVisible.value = true;
          else if (entry.target === featuresRef.value) featuresVisible.value = true;
          else if (entry.target === ctaButtonRef.value) ctaButtonVisible.value = true;
          else if (entry.target === trustIndicatorsRef.value) trustIndicatorsVisible.value = true;
          else if (entry.target === userAvatarsRef.value) userAvatarsVisible.value = true;
        } else {
          // Optional: Reset visibility when element leaves viewport
          if (entry.target === ctaContainerRef.value) ctaContainerVisible.value = false;
          else if (entry.target === headlineRef.value) headlineVisible.value = false;
          else if (entry.target === subheadlineRef.value) subheadlineVisible.value = false;
          else if (entry.target === featuresRef.value) featuresVisible.value = false;
          else if (entry.target === ctaButtonRef.value) ctaButtonVisible.value = false;
          else if (entry.target === trustIndicatorsRef.value) trustIndicatorsVisible.value = false;
          else if (entry.target === userAvatarsRef.value) userAvatarsVisible.value = false;
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
    ctaContainerRef.value,
    headlineRef.value,
    subheadlineRef.value,
    featuresRef.value,
    ctaButtonRef.value,
    trustIndicatorsRef.value,
    userAvatarsRef.value
  ].filter(el => el);
  
  elements.forEach(el => observer.observe(el));
});

onUnmounted(() => {
  if (observer) {
    observer.disconnect();
  }
});
</script>

<template>
  <!-- Enhanced Contact/CTA section -->
  <section id="contacts">
  <div class="my-28 w-[90%] max-w-6xl mx-auto">
    <div 
      ref="ctaContainerRef"
      :class="[
        'relative overflow-hidden rounded-2xl shadow-xl shadow-indigo-800/30 hover:shadow-indigo-800/50 transition-all duration-300 group',
        'transform transition-all duration-1000 ease-out',
        ctaContainerVisible ? 'opacity-100 scale-100' : 'opacity-0 scale-95'
      ]"
    >
      <!-- Gradient background with subtle pattern -->
      <div class="absolute inset-0 bg-[url('data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAlIiBoZWlnaHQ9IjEwMCUiPjxkZWZzPjxwYXR0ZXJuIGlkPSJwYXR0ZXJuIiB3aWR0aD0iNDAiIGhlaWdodD0iNDAiIHBhdHRlcm5Vbml0cz0idXNlclNwYWNlT25Vc2UiIHBhdHRlcm5UcmFuc2Zvcm09InJvdGF0ZSg0NSkiPjxyZWN0IHdpZHRoPSIyMCIgaGVpZ2h0PSIyMCIgZmlsbD0icmdiYSgyNTUsMjU1LDI1NSwwLjA1KSIvPjwvcGF0dGVybj48L2RlZnM+PHJlY3Qgd2lkdGg9IjEwMCUiIGhlaWdodD0iMTAwJSIgZmlsbD0idXJsKCNwYXR0ZXJuKSIvPjwvc3ZnPg==')] pattern-animate"></div>
      
      <!-- Main content container -->
      <div class="relative bg-gradient-to-r from-indigo-600 to-violet-600 flex flex-col gap-8 p-12 items-center text-center rounded-2xl">
        <!-- Headline with animated underline -->
        <div 
          ref="headlineRef"
          :class="[
            'space-y-4 max-w-3xl transition-all duration-1000 ease-out',
            headlineVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
          ]"
        >
          <h2 class="text-4xl md:text-5xl font-bold text-white">
            Ready to <span class="relative whitespace-nowrap">
              <span class="relative z-10">join the future</span>
              <span class="absolute bottom-0 left-0 w-full h-3 bg-indigo-300/40 -rotate-1 -z-0"></span>
            </span> of commerce?
          </h2>
          <div 
            ref="subheadlineRef"
            :class="[
              'transition-all duration-1000 ease-out delay-200',
              subheadlineVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
            ]"
          >
            <p class="text-xl text-indigo-100/90">
              Transform your business with our powerful platform trusted by thousands of sellers worldwide.
            </p>
          </div>
        </div>

        <!-- Features list -->
        <div 
          ref="featuresRef"
          :class="[
            'flex flex-wrap justify-center gap-4 md:gap-8 mt-4 transition-all duration-1000 ease-out delay-300',
            featuresVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
          ]"
        >
          <div 
            v-for="(feature, index) in features" 
            :key="index" 
            :class="[
              'flex items-center gap-2 bg-white/10 backdrop-blur-sm px-4 py-2 rounded-full border border-white/10',
              'transition-all duration-700 ease-out',
              featuresVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
            ]"
            :style="{'transition-delay': `${100 + (index * 100)}ms`}"
          >
            <component :is="feature.icon" class="w-5 h-5 text-white" />
            <span class="text-white text-sm md:text-base">{{ feature.text }}</span>
          </div>
        </div>

        <!-- CTA Button with hover animation -->
        <button 
          ref="ctaButtonRef"
          :class="[
            'group relative mt-6 bg-gradient-to-r from-indigo-100 to-indigo-300 hover:from-white hover:to-indigo-100 py-4 px-8 rounded-2xl text-xl text-indigo-700 font-semibold shadow-lg shadow-violet-800/40 hover:shadow-violet-800/60 transition-all duration-300 overflow-hidden hover:cursor-pointer',
            'transform transition-all duration-1000 ease-out delay-500',
            ctaButtonVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
          ]"
        >
          <span class="relative z-10 flex items-center gap-2">
            Get Started Now
            <ArrowRight class="w-5 h-5 transition-transform duration-300 group-hover:translate-x-1" />
          </span>
          <span class="absolute inset-0 bg-gradient-to-r from-white to-indigo-100 opacity-0 group-hover:opacity-100 transition-opacity duration-300 z-0"></span>
        </button>

        <!-- Trust indicators -->
        <div 
          ref="trustIndicatorsRef"
          :class="[
            'flex flex-col items-center gap-2 mt-4 text-indigo-100/80 text-sm transition-all duration-1000 ease-out delay-600',
            trustIndicatorsVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
          ]"
        >
          <div 
            :class="[
              'transition-all duration-1000 ease-out',
              trustIndicatorsVisible ? 'opacity-100' : 'opacity-0'
            ]"
          >
            <p>No credit card required • 7-day free trial</p>
          </div>
          <div 
            ref="userAvatarsRef"
            :class="[
              'flex items-center gap-1 transition-all duration-1000 ease-out delay-200',
              userAvatarsVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
            ]"
          >
            <div class="flex -space-x-2">
              <img src="https://randomuser.me/api/portraits/women/44.jpg" class="w-8 h-8 rounded-full border-2 border-white" alt="User">
              <img src="https://randomuser.me/api/portraits/men/32.jpg" class="w-8 h-8 rounded-full border-2 border-white" alt="User">
              <img src="https://randomuser.me/api/portraits/women/68.jpg" class="w-8 h-8 rounded-full border-2 border-white" alt="User">
            </div>
            <span>Join 10,000+ happy sellers</span>
          </div>
        </div>
      </div>
    </div>
  </div>
  </section>
</template>

<style>
@keyframes pattern-move {
  0% { background-position: 0 0; }
  100% { background-position: 40px 40px; }
}

.group:hover .pattern-animate {
  animation: pattern-move 3s linear infinite;
}
</style>
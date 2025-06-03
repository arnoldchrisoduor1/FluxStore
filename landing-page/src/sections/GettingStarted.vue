<script setup>
import { 
  UserRound, 
  Store, 
  FileEdit, 
  MousePointerClick, 
  Eye,
  Check 
} from 'lucide-vue-next';
import { ref, onMounted } from 'vue';

// Import your images - adjust paths as needed based on your project structure
import registerImg from '../assets/images/register.png';
import profilePageImg from '../assets/images/profile-page.png';
import createShopTopImg from '../assets/images/create-shop-top.png';
import createShopBottomImg from '../assets/images/create-shop-bottom.png';
import shopImg from '../assets/images/shop.png';

const steps = ref([
  {
    title: "Register for an Account",
    description: "Create your personal account in less than 2 minutes",
    icon: UserRound,
    image: registerImg
  },
  {
    title: "Create Shop",
    description: "Access your dashboard and initiate shop creation",
    icon: Store,
    image: profilePageImg
  },
  {
    title: "Fill Shop Details",
    description: "Provide your shop information and upload branding",
    icon: FileEdit,
    image: createShopTopImg
  },
  {
    title: "Click Create Shop",
    description: "Finalize and launch your digital storefront",
    icon: MousePointerClick,
    image: createShopBottomImg
  },
  {
    title: "View Your Shop",
    description: "Your shop is now live and ready for customers!",
    icon: Eye,
    image: shopImg
  }
]);

const activeStep = ref(0);

onMounted(() => {
  // Auto-advance steps for demo purposes (remove if not needed)
  const interval = setInterval(() => {
    activeStep.value = (activeStep.value + 1) % steps.value.length;
  }, 4000);
  return () => clearInterval(interval);
});
</script>

<template>
  <div class="py-16 px-4 sm:px-6 lg:px-8 bg-gradient-to-b from-white to-indigo-50/30">
    <div class="max-w-6xl mx-auto">
      <div class="text-center flex flex-col justify-center items-center gap-5 mb-12">
        <div class="border border-indigo-200 px-4 py-1.5 rounded-full bg-gradient-to-r from-indigo-100 to-violet-100 shadow-sm">
          <p class="text-indigo-700 font-medium">Getting Started</p>
        </div>
        <h2 class="text-4xl font-bold text-indigo-900">How to Set Up Your Shop</h2>
        <p class="text-violet-700 max-w-2xl text-lg">
          Launch your online store in just 5 simple steps. Our platform makes it effortless to get started.
        </p>
      </div>

      <!-- Step Navigation -->
      <div class="flex justify-center mb-12">
        <div class="relative w-full max-w-4xl">
          <!-- Progress bar -->
          <div class="absolute top-1/2 left-0 right-0 h-1 bg-indigo-100 transform -translate-y-1/2 z-0"></div>
          <div 
            class="absolute top-1/2 left-0 h-1 bg-gradient-to-r from-violet-500 to-indigo-600 transform -translate-y-1/2 z-10 transition-all duration-500 ease-in-out" 
            :style="{ width: `${(activeStep / (steps.length - 1)) * 100}%` }"
          ></div>
          
          <!-- Step indicators -->
          <div class="relative flex justify-between z-20">
            <button
              v-for="(step, index) in steps"
              :key="index"
              @click="activeStep = index"
              class="flex flex-col items-center group"
            >
              <div 
                class="w-12 h-12 rounded-full flex items-center justify-center mb-2 transition-all duration-300"
                :class="{
                  'bg-gradient-to-br from-violet-500 to-indigo-600 text-white shadow-lg shadow-violet-200': activeStep >= index,
                  'bg-white border-2 border-indigo-200 text-indigo-300 group-hover:border-indigo-300 group-hover:text-indigo-400': activeStep < index
                }"
              >
                <component :is="step.icon" class="w-5 h-5" />
              </div>
              <span 
                class="text-sm font-medium transition-colors"
                :class="{
                  'text-indigo-800': activeStep >= index,
                  'text-indigo-400': activeStep < index
                }"
              >
                Step {{ index + 1 }}
              </span>
            </button>
          </div>
        </div>
      </div>

      <!-- Step Content -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
        <!-- Text Content -->
        <div class="space-y-6">
          <div class="flex items-center gap-3">
            <div class="bg-gradient-to-br from-violet-500 to-indigo-600 text-white text-lg font-bold w-10 h-10 rounded-full flex items-center justify-center">
              {{ activeStep + 1 }}
            </div>
            <h3 class="text-2xl font-bold bg-gradient-to-r from-violet-500 to-indigo-700 text-transparent bg-clip-text">
              {{ steps[activeStep].title }}
            </h3>
          </div>
          <p class="text-indigo-700 text-lg">
            {{ steps[activeStep].description }}
          </p>
          <ul class="space-y-3">
            <li v-if="activeStep === 0" class="flex items-start gap-2 text-indigo-700">
              <Check class="w-5 h-5 text-violet-500 mt-0.5 flex-shrink-0" />
              <span>No credit card required</span>
            </li>
            <li v-if="activeStep === 1" class="flex items-start gap-2 text-indigo-700">
              <Check class="w-5 h-5 text-violet-500 mt-0.5 flex-shrink-0" />
              <span>Access powerful dashboard tools</span>
            </li>
            <li v-if="activeStep === 2" class="flex items-start gap-2 text-indigo-700">
              <Check class="w-5 h-5 text-violet-500 mt-0.5 flex-shrink-0" />
              <span>Customize your shop appearance</span>
            </li>
            <li v-if="activeStep === 3" class="flex items-start gap-2 text-indigo-700">
              <Check class="w-5 h-5 text-violet-500 mt-0.5 flex-shrink-0" />
              <span>Instant shop activation</span>
            </li>
            <li v-if="activeStep === 4" class="flex items-start gap-2 text-indigo-700">
              <Check class="w-5 h-5 text-violet-500 mt-0.5 flex-shrink-0" />
              <span>Start adding products immediately</span>
            </li>
          </ul>
          <div class="pt-4 flex gap-4">
            <button 
              @click="activeStep = Math.max(0, activeStep - 1)"
              :disabled="activeStep === 0"
              class="px-5 py-2.5 rounded-lg border border-indigo-300 text-indigo-700 font-medium disabled:opacity-50 disabled:cursor-not-allowed hover:bg-indigo-50 transition-colors"
            >
              Previous
            </button>
            <button 
              @click="activeStep = Math.min(steps.length - 1, activeStep + 1)"
              :disabled="activeStep === steps.length - 1"
              class="px-5 py-2.5 rounded-lg bg-gradient-to-r from-violet-500 to-indigo-600 text-white font-medium shadow-md shadow-violet-200 disabled:opacity-50 disabled:cursor-not-allowed hover:opacity-90 transition-opacity"
            >
              Next
            </button>
          </div>
        </div>

        <!-- Image Preview -->
        <div class="relative">
          <div class="border-2 border-violet-200 rounded-xl shadow-xl overflow-hidden bg-white">
            <img 
              :src="steps[activeStep].image" 
              class="w-full h-auto object-contain transition-opacity duration-500"
              :alt="steps[activeStep].title"
            />
          </div>
          <div class="absolute -bottom-4 -right-4 bg-white px-3 py-1.5 rounded-lg shadow-md border border-indigo-100 text-sm font-medium text-indigo-700">
            Step {{ activeStep + 1 }} of {{ steps.length }}
          </div>
        </div>
      </div>

      <!-- Quick Start CTA -->
      <div class="mt-20 text-center">
        <h3 class="text-2xl font-bold text-indigo-900 mb-4">Ready to Get Started?</h3>
        <p class="text-indigo-700 max-w-2xl mx-auto mb-6">
          Join thousands of sellers who've transformed their businesses with our platform.
        </p>
        <button class="px-8 py-3.5 rounded-full bg-gradient-to-r from-violet-500 to-indigo-600 text-white font-bold shadow-lg shadow-violet-200 hover:shadow-xl hover:shadow-violet-300 transition-all duration-300">
          Create Your Free Account Now
        </button>
      </div>
    </div>
  </div>
</template>

<style>
/* Smooth transitions for step content */
.step-enter-active,
.step-leave-active {
  transition: all 0.5s ease;
}
.step-enter-from,
.step-leave-to {
  opacity: 0;
  transform: translateY(10px);
}
</style>
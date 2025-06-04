<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import { ChevronRight, Mail, Twitter, Facebook, Linkedin, Github } from 'lucide-vue-next';

const links = {
  about: [
    { name: "Our Product" },
    { name: "Features" },
    { name: "Getting Started" },
    { name: "Testimonials" }
  ],
  payments: [
    { name: "Pricing" },
    { name: "Blockchain" },
    { name: "Secure Transactions" },
    { name: "Crypto Payments" }
  ],
  support: [
    { name: "Help Center" },
    { name: "Community" },
    { name: "Developers" },
    { name: "Status" }
  ]
};

const socialLinks = [
  { icon: Twitter, url: "#" },
  { icon: Facebook, url: "#" },
  { icon: Linkedin, url: "#" },
  { icon: Github, url: "#" }
];

// Refs for each animated section
const brandRef = ref(null);
const aboutRef = ref(null);
const paymentsRef = ref(null);
const supportRef = ref(null);
const newsletterRef = ref(null);
const dividerRef = ref(null);
const bottomRef = ref(null);

// Visibility states
const brandVisible = ref(false);
const aboutVisible = ref(false);
const paymentsVisible = ref(false);
const supportVisible = ref(false);
const newsletterVisible = ref(false);
const dividerVisible = ref(false);
const bottomVisible = ref(false);

// Intersection Observer
let observer = null;

const createObserver = () => {
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          if (entry.target === brandRef.value) brandVisible.value = true;
          else if (entry.target === aboutRef.value) aboutVisible.value = true;
          else if (entry.target === paymentsRef.value) paymentsVisible.value = true;
          else if (entry.target === supportRef.value) supportVisible.value = true;
          else if (entry.target === newsletterRef.value) newsletterVisible.value = true;
          else if (entry.target === dividerRef.value) dividerVisible.value = true;
          else if (entry.target === bottomRef.value) bottomVisible.value = true;
        } else {
          // Optional: Reset animations when out of view
          if (entry.target === brandRef.value) brandVisible.value = false;
          else if (entry.target === aboutRef.value) aboutVisible.value = false;
          else if (entry.target === paymentsRef.value) paymentsVisible.value = false;
          else if (entry.target === supportRef.value) supportVisible.value = false;
          else if (entry.target === newsletterRef.value) newsletterVisible.value = false;
          else if (entry.target === dividerRef.value) dividerVisible.value = false;
          else if (entry.target === bottomRef.value) bottomVisible.value = false;
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
  
  const elements = [
    brandRef.value,
    aboutRef.value,
    paymentsRef.value,
    supportRef.value,
    newsletterRef.value,
    dividerRef.value,
    bottomRef.value
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
  <footer class="bg-gradient-to-b from-indigo-800 to-violet-900 pt-12 pb-6 px-4 sm:px-6 lg:px-8">
    <div class="max-w-7xl mx-auto">
      <!-- Top Section -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-10">
        <!-- Brand Info -->
        <div 
          ref="brandRef"
          :class="[
            'space-y-6 transition-all duration-800 ease-out',
            brandVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
          ]"
        >
          <h1 class="text-3xl font-bold text-white">FluxStore</h1>
          <p 
            :class="[
              'text-indigo-200 text-lg leading-relaxed transition-all duration-800 ease-out delay-200',
              brandVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-6'
            ]"
          >
            Revolutionizing commerce through AI and Blockchain Technology
          </p>
          
          <!-- Social Links -->
          <div class="flex space-x-4">
            <a 
              v-for="(social, index) in socialLinks" 
              :key="index" 
              :href="social.url" 
              :class="[
                'text-indigo-200 hover:text-white transition-all duration-300 ease-out',
                brandVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-4'
              ]"
              :style="{ 
                transitionDelay: brandVisible ? `${400 + index * 100}ms` : '0ms',
                transitionDuration: '600ms'
              }"
            >
              <component :is="social.icon" class="w-5 h-5" />
            </a>
          </div>
        </div>

        <!-- About Section -->
        <div 
          ref="aboutRef"
          :class="[
            'space-y-4 transition-all duration-800 ease-out delay-100',
            aboutVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
          ]"
        >
          <h2 class="text-lg font-semibold text-white uppercase tracking-wider">
            About
          </h2>
          <ul class="space-y-3">
            <li 
              v-for="(link, index) in links.about" 
              :key="index" 
              :class="[
                'group flex items-start hover:text-white transition-all duration-600 ease-out',
                aboutVisible ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-4'
              ]"
              :style="{ 
                transitionDelay: aboutVisible ? `${200 + index * 100}ms` : '0ms'
              }"
            >
              <ChevronRight class="text-indigo-300 h-4 w-4 mt-1 flex-shrink-0 group-hover:text-white group-hover:translate-x-1 transition-transform" />
              <a href="#" class="text-indigo-300 group-hover:text-white ml-2">{{ link.name }}</a>
            </li>
          </ul>
        </div>

        <!-- Payments Section -->
        <div 
          ref="paymentsRef"
          :class="[
            'space-y-4 transition-all duration-800 ease-out delay-200',
            paymentsVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
          ]"
        >
          <h2 class="text-lg font-semibold text-white uppercase tracking-wider">
            Payments
          </h2>
          <ul class="space-y-3">
            <li 
              v-for="(link, index) in links.payments" 
              :key="index" 
              :class="[
                'group flex items-start hover:text-white transition-all duration-600 ease-out',
                paymentsVisible ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-4'
              ]"
              :style="{ 
                transitionDelay: paymentsVisible ? `${200 + index * 100}ms` : '0ms'
              }"
            >
              <ChevronRight class="text-indigo-300 h-4 w-4 mt-1 flex-shrink-0 group-hover:text-white group-hover:translate-x-1 transition-transform" />
              <a href="#" class="text-indigo-300 group-hover:text-white ml-2">{{ link.name }}</a>
            </li>
          </ul>
        </div>

        <!-- Support Section -->
        <div 
          ref="supportRef"
          :class="[
            'space-y-4 transition-all duration-800 ease-out delay-300',
            supportVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
          ]"
        >
          <h2 class="text-lg font-semibold text-white uppercase tracking-wider">
            Support
          </h2>
          <ul class="space-y-3">
            <li 
              v-for="(link, index) in links.support" 
              :key="index" 
              :class="[
                'group flex items-start hover:text-white transition-all duration-600 ease-out',
                supportVisible ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-4'
              ]"
              :style="{ 
                transitionDelay: supportVisible ? `${200 + index * 100}ms` : '0ms'
              }"
            >
              <ChevronRight class="text-indigo-300 h-4 w-4 mt-1 flex-shrink-0 group-hover:text-white group-hover:translate-x-1 transition-transform" />
              <a href="#" class="text-indigo-300 group-hover:text-white ml-2">{{ link.name }}</a>
            </li>
          </ul>
        </div>

        <!-- Newsletter -->
        <div 
          ref="newsletterRef"
          :class="[
            'space-y-4 transition-all duration-800 ease-out delay-400',
            newsletterVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-8'
          ]"
        >
          <h2 class="text-lg font-semibold text-white uppercase tracking-wider">
            Newsletter
          </h2>
          <p 
            :class="[
              'text-indigo-200 transition-all duration-600 ease-out delay-200',
              newsletterVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-4'
            ]"
          >
            Subscribe to get updates on new features and releases
          </p>
          <form class="space-y-3">
            <div 
              :class="[
                'relative transition-all duration-600 ease-out delay-400',
                newsletterVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-4'
              ]"
            >
              <Mail class="absolute left-3 top-1/2 transform -translate-y-1/2 text-indigo-300 w-5 h-5" />
              <input
                type="email"
                placeholder="Your email address"
                class="w-full bg-violet-700/30 border border-indigo-400/30 rounded-lg py-3 pl-10 pr-4 text-white placeholder-indigo-300 focus:outline-none focus:ring-2 focus:ring-indigo-400 focus:border-transparent"
              />
            </div>
            <button
              type="submit"
              :class="[
                'w-full bg-gradient-to-r from-indigo-400 to-violet-500 hover:from-indigo-300 hover:to-violet-400 text-white font-semibold py-3 px-6 rounded-lg transition-all duration-300 shadow-lg hover:shadow-indigo-500/20 ease-out delay-600',
                newsletterVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-4'
              ]"
            >
              Subscribe
            </button>
          </form>
        </div>
      </div>

      <!-- Divider -->
      <div 
        ref="dividerRef"
        :class="[
          'border-t border-indigo-700/50 my-8 transition-all duration-800 ease-out',
          dividerVisible ? 'opacity-100 scale-x-100' : 'opacity-0 scale-x-0'
        ]"
      ></div>

      <!-- Bottom Section -->
      <div 
        ref="bottomRef"
        :class="[
          'flex flex-col md:flex-row justify-between items-center transition-all duration-800 ease-out',
          bottomVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-6'
        ]"
      >
        <p 
          :class="[
            'text-indigo-300 text-sm transition-all duration-600 ease-out delay-200',
            bottomVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-4'
          ]"
        >
          &copy; 2025 FluxStore. All rights reserved.
        </p>
        <div class="flex space-x-6 mt-4 md:mt-0">
          <a 
            v-for="(link, index) in ['Privacy Policy', 'Terms of Service', 'Cookies']" 
            :key="index" 
            href="#" 
            :class="[
              'text-indigo-300 hover:text-white text-sm transition-all duration-600 ease-out',
              bottomVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-4'
            ]"
            :style="{ 
              transitionDelay: bottomVisible ? `${400 + index * 100}ms` : '0ms'
            }"
          >
            {{ link }}
          </a>
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
/* Smooth transitions for hover effects */
a {
  transition: color 0.2s ease;
}

/* Better focus states for accessibility */
input:focus {
  box-shadow: 0 0 0 3px rgba(129, 140, 248, 0.5);
}

/* Transform origin for divider scale animation */
.border-t {
  transform-origin: left center;
}
</style>
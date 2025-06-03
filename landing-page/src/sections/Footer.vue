<script setup>
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
</script>

<template>
  <footer class="bg-gradient-to-b from-indigo-800 to-violet-900 pt-12 pb-6 px-4 sm:px-6 lg:px-8">
    <div class="max-w-7xl mx-auto">
      <!-- Top Section -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-10">
        <!-- Brand Info -->
        <div class="space-y-6">
          <h1 class="text-3xl font-bold text-white">FluxStore</h1>
          <p class="text-indigo-200 text-lg leading-relaxed">
            Revolutionizing commerce through AI and Blockchain Technology
          </p>
          
          <!-- Social Links -->
          <div class="flex space-x-4">
            <a v-for="(social, index) in socialLinks" :key="index" :href="social.url" 
               class="text-indigo-200 hover:text-white transition-colors duration-300">
              <component :is="social.icon" class="w-5 h-5" />
            </a>
          </div>
        </div>

        <!-- Links Sections -->
        <div v-for="(section, key) in links" :key="key" class="space-y-4">
          <h2 class="text-lg font-semibold text-white uppercase tracking-wider">
            {{ key }}
          </h2>
          <ul class="space-y-3">
            <li v-for="(link, index) in section" :key="index" 
                class="group flex items-start hover:text-white transition-colors duration-200">
              <ChevronRight class="text-indigo-300 h-4 w-4 mt-1 flex-shrink-0 group-hover:text-white group-hover:translate-x-1 transition-transform" />
              <a href="#" class="text-indigo-300 group-hover:text-white ml-2">{{ link.name }}</a>
            </li>
          </ul>
        </div>

        <!-- Newsletter -->
        <div class="space-y-4">
          <h2 class="text-lg font-semibold text-white uppercase tracking-wider">
            Newsletter
          </h2>
          <p class="text-indigo-200">
            Subscribe to get updates on new features and releases
          </p>
          <form class="space-y-3">
            <div class="relative">
              <Mail class="absolute left-3 top-1/2 transform -translate-y-1/2 text-indigo-300 w-5 h-5" />
              <input
                type="email"
                placeholder="Your email address"
                class="w-full bg-violet-700/30 border border-indigo-400/30 rounded-lg py-3 pl-10 pr-4 text-white placeholder-indigo-300 focus:outline-none focus:ring-2 focus:ring-indigo-400 focus:border-transparent"
              />
            </div>
            <button
              type="submit"
              class="w-full bg-gradient-to-r from-indigo-400 to-violet-500 hover:from-indigo-300 hover:to-violet-400 text-white font-semibold py-3 px-6 rounded-lg transition-all duration-300 shadow-lg hover:shadow-indigo-500/20"
            >
              Subscribe
            </button>
          </form>
        </div>
      </div>

      <!-- Divider -->
      <div class="border-t border-indigo-700/50 my-8"></div>

      <!-- Bottom Section -->
      <div class="flex flex-col md:flex-row justify-between items-center">
        <p class="text-indigo-300 text-sm">
          &copy; 2025 FluxStore. All rights reserved.
        </p>
        <div class="flex space-x-6 mt-4 md:mt-0">
          <a href="#" class="text-indigo-300 hover:text-white text-sm">Privacy Policy</a>
          <a href="#" class="text-indigo-300 hover:text-white text-sm">Terms of Service</a>
          <a href="#" class="text-indigo-300 hover:text-white text-sm">Cookies</a>
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
</style>
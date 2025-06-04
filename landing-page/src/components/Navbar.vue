<script setup>
import { ref } from "vue";
import { AlignJustify, X, Bell, Home, Info, Zap, Users, Mail, ChevronRight } from "lucide-vue-next";

const isMenuOpen = ref(false);
const activeSection = ref('home');

const navItems = [
  { id: "home", name: "Home", icon: Home, path: "#home" },
  { id: "about", name: "About", icon: Info, path: "#about" },
  { id: "features", name: "Features", icon: Zap, path: "#features" },
  { id: "team", name: "Team", icon: Users, path: "#team" },
  { id: "contacts", name: "Contacts", icon: Mail, path: "#contacts" },
];

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};

const setActiveSection = (section) => {
  activeSection.value = section;
};
</script>

<template>
  <!-- Navbar -->
  <nav class="fixed top-0 left-0 right-0 z-40 backdrop-blur-md bg-white/80 shadow-sm">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16">
        <!-- Logo -->
        <div class="flex-shrink-0">
          <a href="#home" class="flex items-center">
            <span class="bg-gradient-to-r from-indigo-600 to-violet-600 font-bold text-2xl text-transparent bg-clip-text">
              FluxStore
            </span>
          </a>
        </div>

        <!-- Desktop Navigation -->
        <div class="hidden md:block">
          <div class="ml-10 flex items-center space-x-6">
            <a
              v-for="item in navItems"
              :key="item.id"
              :href="item.path"
              @click="setActiveSection(item.id)"
              class="relative px-3 py-2 text-sm font-medium transition-all duration-300 group"
              :class="activeSection === item.id ? 'text-indigo-600' : 'text-gray-600 hover:text-violet-600'"
            >
              {{ item.name }}
              <span 
                v-if="activeSection === item.id"
                class="absolute inset-x-1 -bottom-1 h-0.5 bg-gradient-to-r from-indigo-500 to-violet-500 rounded-full"
              ></span>
              <span 
                v-else
                class="absolute inset-x-1 -bottom-1 h-0.5 bg-gradient-to-r from-indigo-500/0 to-violet-500/0 rounded-full group-hover:from-indigo-500/50 group-hover:to-violet-500/50 transition-all duration-300"
              ></span>
            </a>
          </div>
        </div>

        <!-- Right side icons -->
        <div class="flex items-center gap-4">
          <button class="p-1 rounded-full text-gray-600 hover:text-violet-600 hover:bg-violet-50 transition-colors duration-200 hover:cursor-pointer">
            <Bell class="w-5 h-5" />
          </button>
          
          <!-- Mobile menu button -->
          <button 
            @click="toggleMenu"
            class="md:hidden p-1 rounded-full text-gray-600 hover:text-violet-600 hover:bg-violet-50 transition-colors duration-200 focus:outline-none hover:cursor-pointer"
          >
            <AlignJustify v-if="!isMenuOpen" class="w-6 h-6" />
          </button>
        </div>
      </div>
    </div>
  </nav>

  <!-- Mobile Sidebar -->
  <Transition name="sidebar">
    <div v-if="isMenuOpen" class="md:hidden">
      <!-- Overlay -->
      <div 
        class="fixed inset-0 bg-black/50 z-40 transition-opacity duration-300"
        @click="toggleMenu"
      ></div>
      
      <!-- Sidebar Content -->
      <div class="fixed inset-y-0 right-0 w-80 max-w-full z-50">
        <div class="h-full bg-gradient-to-b from-indigo-50 to-violet-50 shadow-xl overflow-y-auto">
          <div class="flex items-center justify-between p-4 border-b border-indigo-100/50">
            <a href="#home" class="flex items-center" @click="toggleMenu">
              <span class="bg-gradient-to-r from-indigo-600 to-violet-600 font-bold text-2xl text-transparent bg-clip-text">
                FluxStore
              </span>
            </a>
            <button 
              @click="toggleMenu"
              class="p-1 rounded-full text-gray-500 hover:text-violet-600 hover:bg-violet-100 transition-colors duration-200 z-20 hover:cursor-pointer"
            >
              <X class="w-6 h-6" />
            </button>
          </div>
          
          <nav class="px-4 py-6">
            <ul class="space-y-2">
              <li v-for="item in navItems" :key="item.id">
                <a
                  :href="item.path"
                  @click="() => { setActiveSection(item.id); toggleMenu(); }"
                  class="group flex items-center justify-between px-4 py-3 rounded-lg transition-all duration-200"
                  :class="activeSection === item.id 
                    ? 'bg-gradient-to-r from-indigo-500/10 to-violet-500/10 border-l-4 border-indigo-500 text-indigo-600' 
                    : 'text-gray-600 hover:bg-violet-100/50 hover:text-violet-600'"
                >
                  <div class="flex items-center">
                    <component 
                      :is="item.icon" 
                      class="w-5 h-5 mr-3"
                      :class="activeSection === item.id ? 'text-indigo-500' : 'text-gray-400 group-hover:text-violet-500'"
                    />
                    <span class="font-medium">{{ item.name }}</span>
                  </div>
                  <ChevronRight class="w-4 h-4 text-gray-400 group-hover:text-violet-500" />
                </a>
              </li>
            </ul>
            
            <div class="mt-8 px-4">
              <button 
                class="w-full py-3 px-6 rounded-lg bg-gradient-to-r from-indigo-600 to-violet-600 text-white font-medium shadow-lg hover:shadow-xl transition-all duration-300 hover:from-indigo-500 hover:to-violet-500 focus:outline-none focus:ring-2 focus:ring-violet-500 focus:ring-offset-2"
                @click="toggleMenu"
              >
                Get Started
              </button>
            </div>
          </nav>
          
          <!-- Decorative elements -->
          <div class="absolute bottom-0 left-0 right-0 h-32 bg-gradient-to-t from-indigo-100/80 to-transparent pointer-events-none"></div>
          <div class="absolute -bottom-20 -left-20 w-64 h-64 rounded-full bg-violet-200/30 blur-xl"></div>
          <div class="absolute -top-20 -right-20 w-64 h-64 rounded-full bg-indigo-200/30 blur-xl"></div>
        </div>
      </div>
    </div>
  </Transition>

  <!-- Main Content -->
  <main class="pt-16">
    <!-- Your page sections with #home, #about, etc. will go here -->
  </main>
</template>

<style>
/* Sidebar transition */
.sidebar-enter-active,
.sidebar-leave-active {
  transition: opacity 0.3s ease;
}

.sidebar-enter-from,
.sidebar-leave-to {
  opacity: 0;
}

.sidebar-enter-active .fixed.right-0,
.sidebar-leave-active .fixed.right-0 {
  transition: transform 0.3s ease;
}

.sidebar-enter-from .fixed.right-0 {
  transform: translateX(100%);
}

.sidebar-enter-to .fixed.right-0 {
  transform: translateX(0);
}

.sidebar-leave-to .fixed.right-0 {
  transform: translateX(100%);
}

/* Smooth scrolling */
html {
  scroll-behavior: smooth;
}
</style>
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
    <Transition name="fade-slide-up" appear>
      <div class="max-w-7xl mx-auto">
        <!-- Top Section -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-10">
          <!-- Brand Info -->
          <Transition name="fade-slide-up" appear>
            <div class="space-y-6">
              <h1 class="text-3xl font-bold text-white">FluxStore</h1>
              <Transition name="fade-slide-up" appear>
                <p class="text-indigo-200 text-lg leading-relaxed">
                  Revolutionizing commerce through AI and Blockchain Technology
                </p>
              </Transition>
              
              <!-- Social Links -->
              <Transition name="staggered-fade" appear>
                <div class="flex space-x-4">
                  <Transition 
                    v-for="(social, index) in socialLinks" 
                    :key="index" 
                    name="social-item"
                    appear
                    :style="{'--stagger-order': index}"
                  >
                    <a :href="social.url" 
                       class="text-indigo-200 hover:text-white transition-colors duration-300">
                      <component :is="social.icon" class="w-5 h-5" />
                    </a>
                  </Transition>
                </div>
              </Transition>
            </div>
          </Transition>

          <!-- Links Sections -->
          <TransitionGroup name="fade-slide-up" appear tag="div" class="contents">
            <Transition 
              v-for="(section, key, idx) in links" 
              :key="key" 
              appear
              :style="{'--stagger-order': idx}"
              name="section-item"
              class="contents"
            >
              <div class="space-y-4">
                <h2 class="text-lg font-semibold text-white uppercase tracking-wider">
                  {{ key }}
                </h2>
                <TransitionGroup name="list-item" appear tag="ul" class="space-y-3">
                  <Transition 
                    v-for="(link, index) in section" 
                    :key="index" 
                    appear
                    :style="{'--stagger-order': index}"
                  >
                    <li class="group flex items-start hover:text-white transition-colors duration-200">
                      <ChevronRight class="text-indigo-300 h-4 w-4 mt-1 flex-shrink-0 group-hover:text-white group-hover:translate-x-1 transition-transform" />
                      <a href="#" class="text-indigo-300 group-hover:text-white ml-2">{{ link.name }}</a>
                    </li>
                  </Transition>
                </TransitionGroup>
              </div>
            </Transition>
          </TransitionGroup>

          <!-- Newsletter -->
          <Transition name="fade-slide-up" appear>
            <div class="space-y-4">
              <h2 class="text-lg font-semibold text-white uppercase tracking-wider">
                Newsletter
              </h2>
              <Transition name="fade-slide-up" appear>
                <p class="text-indigo-200">
                  Subscribe to get updates on new features and releases
                </p>
              </Transition>
              <Transition name="fade-slide-up" appear>
                <form class="space-y-3">
                  <div class="relative">
                    <Mail class="absolute left-3 top-1/2 transform -translate-y-1/2 text-indigo-300 w-5 h-5" />
                    <input
                      type="email"
                      placeholder="Your email address"
                      class="w-full bg-violet-700/30 border border-indigo-400/30 rounded-lg py-3 pl-10 pr-4 text-white placeholder-indigo-300 focus:outline-none focus:ring-2 focus:ring-indigo-400 focus:border-transparent"
                    />
                  </div>
                  <Transition name="fade-slide-up" appear>
                    <button
                      type="submit"
                      class="w-full bg-gradient-to-r from-indigo-400 to-violet-500 hover:from-indigo-300 hover:to-violet-400 text-white font-semibold py-3 px-6 rounded-lg transition-all duration-300 shadow-lg hover:shadow-indigo-500/20"
                    >
                      Subscribe
                    </button>
                  </Transition>
                </form>
              </Transition>
            </div>
          </Transition>
        </div>

        <!-- Divider -->
        <Transition name="fade" appear>
          <div class="border-t border-indigo-700/50 my-8"></div>
        </Transition>

        <!-- Bottom Section -->
        <Transition name="fade-slide-up" appear>
          <div class="flex flex-col md:flex-row justify-between items-center">
            <Transition name="fade-slide-up" appear>
              <p class="text-indigo-300 text-sm">
                &copy; 2025 FluxStore. All rights reserved.
              </p>
            </Transition>
            <Transition name="staggered-fade" appear>
              <div class="flex space-x-6 mt-4 md:mt-0">
                <Transition 
                  v-for="(link, index) in ['Privacy Policy', 'Terms of Service', 'Cookies']" 
                  :key="index" 
                  name="footer-link"
                  appear
                  :style="{'--stagger-order': index}"
                >
                  <a href="#" class="text-indigo-300 hover:text-white text-sm">{{ link }}</a>
                </Transition>
              </div>
            </Transition>
          </div>
        </Transition>
      </div>
    </Transition>
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

/* Transition styles */
.fade-slide-up-enter-active {
  transition: all 0.6s ease;
}
.fade-slide-up-leave-active {
  transition: all 0.3s ease;
}
.fade-slide-up-enter-from {
  opacity: 0;
  transform: translateY(20px);
}
.fade-slide-up-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}

.staggered-fade-enter-active {
  transition: all 0.6s ease;
}
.staggered-fade-leave-active {
  transition: all 0.3s ease;
}
.staggered-fade-enter-from {
  opacity: 0;
}
.staggered-fade-leave-to {
  opacity: 0;
}

.social-item-enter-active {
  transition: all 0.5s ease calc(var(--stagger-order) * 0.1s);
}
.social-item-leave-active {
  transition: all 0.3s ease;
}
.social-item-enter-from {
  opacity: 0;
  transform: translateY(10px);
}
.social-item-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}

.section-item-enter-active {
  transition: all 0.6s ease calc(var(--stagger-order) * 0.1s);
}
.section-item-leave-active {
  transition: all 0.3s ease;
}
.section-item-enter-from {
  opacity: 0;
  transform: translateY(15px);
}
.section-item-leave-to {
  opacity: 0;
  transform: translateY(-15px);
}

.list-item-enter-active {
  transition: all 0.5s ease calc(var(--stagger-order) * 0.05s);
}
.list-item-leave-active {
  transition: all 0.3s ease;
}
.list-item-enter-from {
  opacity: 0;
  transform: translateX(10px);
}
.list-item-leave-to {
  opacity: 0;
  transform: translateX(-10px);
}

.footer-link-enter-active {
  transition: all 0.5s ease calc(var(--stagger-order) * 0.1s);
}
.footer-link-leave-active {
  transition: all 0.3s ease;
}
.footer-link-enter-from {
  opacity: 0;
  transform: translateY(5px);
}
.footer-link-leave-to {
  opacity: 0;
  transform: translateY(-5px);
}

.fade-enter-active {
  transition: all 0.6s ease 0.4s;
}
.fade-leave-active {
  transition: all 0.3s ease;
}
.fade-enter-from {
  opacity: 0;
}
.fade-leave-to {
  opacity: 0;
}
</style>
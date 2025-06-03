<script setup>
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
</script>

<template>
  <!-- Enhanced Contact/CTA section -->
  <div class="my-28 w-[90%] max-w-6xl mx-auto">
    <Transition name="scale-in" appear>
      <div class="relative overflow-hidden rounded-2xl shadow-xl shadow-indigo-800/30 hover:shadow-indigo-800/50 transition-all duration-300 group">
        <!-- Gradient background with subtle pattern -->
        <div class="absolute inset-0 bg-[url('data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxMDAlIiBoZWlnaHQ9IjEwMCUiPjxkZWZzPjxwYXR0ZXJuIGlkPSJwYXR0ZXJuIiB3aWR0aD0iNDAiIGhlaWdodD0iNDAiIHBhdHRlcm5Vbml0cz0idXNlclNwYWNlT25Vc2UiIHBhdHRlcm5UcmFuc2Zvcm09InJvdGF0ZSg0NSkiPjxyZWN0IHdpZHRoPSIyMCIgaGVpZ2h0PSIyMCIgZmlsbD0icmdiYSgyNTUsMjU1LDI1NSwwLjA1KSIvPjwvcGF0dGVybj48L2RlZnM+PHJlY3Qgd2lkdGg9IjEwMCUiIGhlaWdodD0iMTAwJSIgZmlsbD0idXJsKCNwYXR0ZXJuKSIvPjwvc3ZnPg==')] pattern-animate"></div>
        
        <!-- Main content container -->
        <div class="relative bg-gradient-to-r from-indigo-600 to-violet-600 flex flex-col gap-8 p-12 items-center text-center rounded-2xl">
          <!-- Headline with animated underline -->
          <Transition name="fade-slide-up" appear>
            <div class="space-y-4 max-w-3xl">
              <h2 class="text-4xl md:text-5xl font-bold text-white">
                Ready to <span class="relative whitespace-nowrap">
                  <span class="relative z-10">join the future</span>
                  <span class="absolute bottom-0 left-0 w-full h-3 bg-indigo-300/40 -rotate-1 -z-0"></span>
                </span> of commerce?
              </h2>
              <Transition name="fade-slide-up" appear>
                <p class="text-xl text-indigo-100/90">
                  Transform your business with our powerful platform trusted by thousands of sellers worldwide.
                </p>
              </Transition>
            </div>
          </Transition>

          <!-- Features list -->
          <Transition name="staggered-fade" appear>
            <div class="flex flex-wrap justify-center gap-4 md:gap-8 mt-4">
              <Transition 
                v-for="(feature, index) in features" 
                :key="index" 
                name="feature-item"
                appear
                :style="{'--stagger-order': index}"
              >
                <div class="flex items-center gap-2 bg-white/10 backdrop-blur-sm px-4 py-2 rounded-full border border-white/10">
                  <component :is="feature.icon" class="w-5 h-5 text-white" />
                  <span class="text-white text-sm md:text-base">{{ feature.text }}</span>
                </div>
              </Transition>
            </div>
          </Transition>

          <!-- CTA Button with hover animation -->
          <Transition name="fade-slide-up" appear>
            <button class="group relative mt-6 bg-gradient-to-r from-indigo-100 to-indigo-300 hover:from-white hover:to-indigo-100 py-4 px-8 rounded-2xl text-xl text-indigo-700 font-semibold shadow-lg shadow-violet-800/40 hover:shadow-violet-800/60 transition-all duration-300 overflow-hidden hover:cursor-pointer">
              <span class="relative z-10 flex items-center gap-2">
                Get Started Now
                <ArrowRight class="w-5 h-5 transition-transform duration-300 group-hover:translate-x-1" />
              </span>
              <span class="absolute inset-0 bg-gradient-to-r from-white to-indigo-100 opacity-0 group-hover:opacity-100 transition-opacity duration-300 z-0"></span>
            </button>
          </Transition>

          <!-- Trust indicators -->
          <Transition name="fade-slide-up" appear>
            <div class="flex flex-col items-center gap-2 mt-4 text-indigo-100/80 text-sm">
              <Transition name="fade" appear>
                <p>No credit card required • 7-day free trial</p>
              </Transition>
              <Transition name="fade-slide-up" appear>
                <div class="flex items-center gap-1">
                  <div class="flex -space-x-2">
                    <img src="https://randomuser.me/api/portraits/women/44.jpg" class="w-8 h-8 rounded-full border-2 border-white" alt="User">
                    <img src="https://randomuser.me/api/portraits/men/32.jpg" class="w-8 h-8 rounded-full border-2 border-white" alt="User">
                    <img src="https://randomuser.me/api/portraits/women/68.jpg" class="w-8 h-8 rounded-full border-2 border-white" alt="User">
                  </div>
                  <span>Join 10,000+ happy sellers</span>
                </div>
              </Transition>
            </div>
          </Transition>
        </div>
      </div>
    </Transition>
  </div>
</template>

<style>
@keyframes pattern-move {
  0% { background-position: 0 0; }
  100% { background-position: 40px 40px; }
}

.group:hover .pattern-animate {
  animation: pattern-move 3s linear infinite;
}

/* Transition styles */
.scale-in-enter-active {
  transition: all 0.8s cubic-bezier(0.22, 1, 0.36, 1);
}
.scale-in-leave-active {
  transition: all 0.3s ease;
}
.scale-in-enter-from {
  opacity: 0;
  transform: scale(0.95);
}
.scale-in-leave-to {
  opacity: 0;
  transform: scale(1.05);
}

.fade-slide-up-enter-active {
  transition: all 0.6s ease 0.2s;
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

.feature-item-enter-active {
  transition: all 0.5s ease calc(var(--stagger-order) * 0.1s);
}
.feature-item-leave-active {
  transition: all 0.3s ease;
}
.feature-item-enter-from {
  opacity: 0;
  transform: translateY(15px) scale(0.95);
}
.feature-item-leave-to {
  opacity: 0;
  transform: translateY(-15px);
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
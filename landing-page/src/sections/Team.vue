<template>
  <section id="team">
  <div class="py-12 px-4 sm:px-6 lg:px-8 bg-gradient-to-b from-indigo-50 to-white">
    <div class="text-center flex flex-col justify-center items-center gap-5 mb-12">
      <Transition name="fadein" appear>
      <div class="border border-indigo-200 px-4 py-1 rounded-full bg-gradient-to-r from-indigo-100 to-violet-100 shadow-sm">
        <p class="text-indigo-700 font-medium">The Team</p>
      </div>
      </Transition>
      <Transition name="fadein" appear>
      <h2 class="text-4xl font-bold text-indigo-900">Meet Our Dream Team</h2>
      </Transition>
      <Transition name="fadeinlag" appear>
      <p class="text-violet-700 max-w-2xl">The passionate professionals driving innovation and excellence in every project we undertake.</p>
      </Transition>
    </div>
    
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 w-[90%] mx-auto max-w-7xl">
      <!-- Team Member 1 -->
       <Transition name="sidefadein" appear>
      <div class="min-h-[400px] border border-violet-200 relative rounded-xl shadow-lg shadow-violet-100 hover:shadow-xl hover:shadow-violet-200 transition-all duration-300 group overflow-hidden hover:cursor-pointer">
        <div class="bg-gradient-to-t from-black/80 via-black/30 to-transparent absolute h-full w-full z-10 rounded-xl"></div>
        <img src="../assets/images/coo.jpg" class="absolute h-full w-full object-cover rounded-xl group-hover:scale-105 transition-transform duration-500" />
        <div class="absolute bottom-0 left-0 p-6 z-20 w-full">
          <h2 class="text-white text-2xl font-bold mb-1">Onyango Omondi</h2>
          <p class="text-violet-200 font-medium">CEO & Founder</p>
          <p class="text-white/80 mt-2 text-sm">Visionary leader with 15+ years of industry experience driving strategic growth.</p>
          <div class="flex gap-3 mt-3">
            <a href="#" class="text-white hover:text-violet-300 transition-colors">
              <icon name="lucide:linkedin" class="w-5 h-5" />
            </a>
            <a href="#" class="text-white hover:text-violet-300 transition-colors">
              <icon name="lucide:twitter" class="w-5 h-5" />
            </a>
          </div>
        </div>
      </div>
      </Transition>
      
      <!-- Team Member 2 -->
       <Transition name="sidefadein" appear>
      <div class="min-h-[400px] border border-violet-200 relative rounded-xl shadow-lg shadow-violet-100 hover:shadow-xl hover:shadow-violet-200 transition-all duration-300 group overflow-hidden hover:cursor-pointer">
        <div class="bg-gradient-to-t from-black/80 via-black/30 to-transparent absolute h-full w-full z-10 rounded-xl"></div>
        <img src="../assets/images/ceo.jpg" class="absolute h-full w-full object-cover rounded-xl group-hover:scale-105 transition-transform duration-500" />
        <div class="absolute bottom-0 left-0 p-6 z-20 w-full">
          <h2 class="text-white text-2xl font-bold mb-1">Sarah Johnson</h2>
          <p class="text-violet-200 font-medium">Chief Operations Officer</p>
          <p class="text-white/80 mt-2 text-sm">Operations expert streamlining processes for maximum efficiency and productivity.</p>
          <div class="flex gap-3 mt-3">
            <a href="#" class="text-white hover:text-violet-300 transition-colors">
              <icon name="lucide:linkedin" class="w-5 h-5" />
            </a>
            <a href="#" class="text-white hover:text-violet-300 transition-colors">
              <icon name="lucide:twitter" class="w-5 h-5" />
            </a>
          </div>
        </div>
      </div>
      </Transition>
      
      <!-- Team Member 3 -->
       <Transition name="sidefadein" appear>
      <div class="min-h-[400px] border border-violet-200 relative rounded-xl shadow-lg shadow-violet-100 hover:shadow-xl hover:shadow-violet-200 transition-all duration-300 group overflow-hidden hover:cursor-pointer">
        <div class="bg-gradient-to-t from-black/80 via-black/30 to-transparent absolute h-full w-full z-10 rounded-xl"></div>
        <img src="../assets/images/marketing.jpg" class="absolute h-full w-full object-cover rounded-xl group-hover:scale-105 transition-transform duration-500" />
        <div class="absolute bottom-0 left-0 p-6 z-20 w-full">
          <h2 class="text-white text-2xl font-bold mb-1">Michael Chen</h2>
          <p class="text-violet-200 font-medium">Marketing Director</p>
          <p class="text-white/80 mt-2 text-sm">Creative strategist building powerful brands and engaging customer experiences.</p>
          <div class="flex gap-3 mt-3">
            <a href="#" class="text-white hover:text-violet-300 transition-colors">
              <icon name="lucide:linkedin" class="w-5 h-5" />
            </a>
            <a href="#" class="text-white hover:text-violet-300 transition-colors">
              <icon name="lucide:instagram" class="w-5 h-5" />
            </a>
          </div>
        </div>
      </div>
      </Transition>
      
      <!-- Team Member 4 -->
       <Transition name="sidefadein" appear>
      <div class="min-h-[400px] border border-violet-200 relative rounded-xl shadow-lg shadow-violet-100 hover:shadow-xl hover:shadow-violet-200 transition-all duration-300 group overflow-hidden hover:cursor-pointer">
        <div class="bg-gradient-to-t from-black/80 via-black/30 to-transparent absolute h-full w-full z-10 rounded-xl"></div>
        <img src="../assets/images/research.jpg" class="absolute h-full w-full object-cover rounded-xl group-hover:scale-105 transition-transform duration-500" />
        <div class="absolute bottom-0 left-0 p-6 z-20 w-full">
          <h2 class="text-white text-2xl font-bold mb-1">Dr. Aisha Bello</h2>
          <p class="text-violet-200 font-medium">Research Lead</p>
          <p class="text-white/80 mt-2 text-sm">Innovation driver with a PhD in Data Science and passion for cutting-edge solutions.</p>
          <div class="flex gap-3 mt-3">
            <a href="#" class="text-white hover:text-violet-300 transition-colors">
              <icon name="lucide:linkedin" class="w-5 h-5" />
            </a>
            <a href="#" class="text-white hover:text-violet-300 transition-colors">
              <icon name="lucide:github" class="w-5 h-5" />
            </a>
          </div>
        </div>
      </div>
       </Transition>
    </div>
  </div>
  </section>
</template>

<style>
  .fadein-enter-active,
.fadein-leave-active {
  transition: opacity 1.5s ease;
  transition: transform 1.5s ease;
}

.fadein-enter-from,
.fadein-leave-to {
  opacity: 0;
  transform: translateY(50px);
}
  .fadeinlag-enter-active,
.fadeinlag-leave-active {
  transition: opacity 1.5s ease;
  transition: transform 1.5s ease;
}

.fadeinlag-enter-from,
.fadeinlag-leave-to {
  opacity: 0;
  transform: translateY(50px);
}

.sidefadein-enter-active,
.sidefadein-leave-active {
  transition: opacity 1.5s ease;
  transition: transform 1.5s ease;
}

.sidefadein-enter-from,
.sidefadein-leave-to {
  opacity: 0;
  transform: translateX(50px);
}
</style>

<script setup>
// If using Nuxt or need to import Lucide icons explicitly
import { Linkedin, Twitter, Instagram, Github } from 'lucide-vue-next';
</script>
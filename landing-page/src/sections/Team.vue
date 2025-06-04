<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import { Linkedin, Twitter, Instagram, Github } from 'lucide-vue-next';

// Refs for each section
const teamTaglineRef = ref(null);
const teamHeadlineRef = ref(null);
const teamSubheadlineRef = ref(null);
const teamMembersRefs = ref([]);

// Visibility states
const teamTaglineVisible = ref(false);
const teamHeadlineVisible = ref(false);
const teamSubheadlineVisible = ref(false);
const teamMembersVisible = ref([]);

// Initialize with false for each team member
onMounted(() => {
  teamMembersVisible.value = Array(4).fill(false);
});

// Intersection Observer instance
let observer = null;

const createObserver = () => {
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          if (entry.target === teamTaglineRef.value) teamTaglineVisible.value = true;
          else if (entry.target === teamHeadlineRef.value) teamHeadlineVisible.value = true;
          else if (entry.target === teamSubheadlineRef.value) teamSubheadlineVisible.value = true;
          else if (teamMembersRefs.value.includes(entry.target)) {
            const index = teamMembersRefs.value.indexOf(entry.target);
            teamMembersVisible.value[index] = true;
          }
        } else {
          // Optional: Reset visibility when element leaves viewport
          if (entry.target === teamTaglineRef.value) teamTaglineVisible.value = false;
          else if (entry.target === teamHeadlineRef.value) teamHeadlineVisible.value = false;
          else if (entry.target === teamSubheadlineRef.value) teamSubheadlineVisible.value = false;
          else if (teamMembersRefs.value.includes(entry.target)) {
            const index = teamMembersRefs.value.indexOf(entry.target);
            teamMembersVisible.value[index] = false;
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
    teamTaglineRef.value,
    teamHeadlineRef.value,
    teamSubheadlineRef.value,
    ...teamMembersRefs.value
  ].filter(el => el);
  
  elements.forEach(el => observer.observe(el));
});

onUnmounted(() => {
  if (observer) {
    observer.disconnect();
  }
});

// Function to set member ref
const setMemberRef = (el, index) => {
  if (el) {
    teamMembersRefs.value[index] = el;
  }
};
</script>

<template>
  <section id="team">
    <div class="py-12 px-4 sm:px-6 lg:px-8 bg-gradient-to-b from-indigo-50 to-white">
      <div class="text-center flex flex-col justify-center items-center gap-5 mb-12">
        <div 
          ref="teamTaglineRef"
          :class="[
            'border border-indigo-200 px-4 py-1 rounded-full bg-gradient-to-r from-indigo-100 to-violet-100 shadow-sm transition-all duration-1000 ease-out',
            teamTaglineVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
          ]"
        >
          <p class="text-indigo-700 font-medium">The Team</p>
        </div>
        
        <h2 
          ref="teamHeadlineRef"
          :class="[
            'text-4xl font-bold text-indigo-900 transition-all duration-1000 ease-out delay-200',
            teamHeadlineVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
          ]"
        >
          Meet Our Dream Team
        </h2>
        
        <p 
          ref="teamSubheadlineRef"
          :class="[
            'text-violet-700 max-w-2xl transition-all duration-1000 ease-out delay-400',
            teamSubheadlineVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
          ]"
        >
          The passionate professionals driving innovation and excellence in every project we undertake.
        </p>
      </div>
      
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 w-[90%] mx-auto max-w-7xl">
        <!-- Team Member 1 -->
        <div 
          :ref="el => setMemberRef(el, 0)"
          :class="[
            'min-h-[400px] border border-violet-200 relative rounded-xl shadow-lg shadow-violet-100 hover:shadow-xl hover:shadow-violet-200 transition-all duration-300 group overflow-hidden hover:cursor-pointer',
            'transform transition-all duration-1000 ease-out',
            teamMembersVisible[0] ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-20'
          ]"
          style="transition-delay: 100ms"
        >
          <div class="bg-gradient-to-t from-black/80 via-black/30 to-transparent absolute h-full w-full z-10 rounded-xl"></div>
          <img src="../assets/images/coo.jpg" class="absolute h-full w-full object-cover rounded-xl group-hover:scale-105 transition-transform duration-500" />
          <div class="absolute bottom-0 left-0 p-6 z-20 w-full">
            <h2 class="text-white text-2xl font-bold mb-1">Onyango Omondi</h2>
            <p class="text-violet-200 font-medium">CEO & Founder</p>
            <p class="text-white/80 mt-2 text-sm">Visionary leader with 15+ years of industry experience driving strategic growth.</p>
            <div class="flex gap-3 mt-3">
              <a href="#" class="text-white hover:text-violet-300 transition-colors">
                <Linkedin class="w-5 h-5" />
              </a>
              <a href="#" class="text-white hover:text-violet-300 transition-colors">
                <Twitter class="w-5 h-5" />
              </a>
            </div>
          </div>
        </div>
        
        <!-- Team Member 2 -->
        <div 
          :ref="el => setMemberRef(el, 1)"
          :class="[
            'min-h-[400px] border border-violet-200 relative rounded-xl shadow-lg shadow-violet-100 hover:shadow-xl hover:shadow-violet-200 transition-all duration-300 group overflow-hidden hover:cursor-pointer',
            'transform transition-all duration-1000 ease-out',
            teamMembersVisible[1] ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-20'
          ]"
          style="transition-delay: 200ms"
        >
          <div class="bg-gradient-to-t from-black/80 via-black/30 to-transparent absolute h-full w-full z-10 rounded-xl"></div>
          <img src="../assets/images/ceo.jpg" class="absolute h-full w-full object-cover rounded-xl group-hover:scale-105 transition-transform duration-500" />
          <div class="absolute bottom-0 left-0 p-6 z-20 w-full">
            <h2 class="text-white text-2xl font-bold mb-1">Joel Johnson</h2>
            <p class="text-violet-200 font-medium">Chief Operations Officer</p>
            <p class="text-white/80 mt-2 text-sm">Operations expert streamlining processes for maximum efficiency and productivity.</p>
            <div class="flex gap-3 mt-3">
              <a href="#" class="text-white hover:text-violet-300 transition-colors">
                <Linkedin class="w-5 h-5" />
              </a>
              <a href="#" class="text-white hover:text-violet-300 transition-colors">
                <Twitter class="w-5 h-5" />
              </a>
            </div>
          </div>
        </div>
        
        <!-- Team Member 3 -->
        <div 
          :ref="el => setMemberRef(el, 2)"
          :class="[
            'min-h-[400px] border border-violet-200 relative rounded-xl shadow-lg shadow-violet-100 hover:shadow-xl hover:shadow-violet-200 transition-all duration-300 group overflow-hidden hover:cursor-pointer',
            'transform transition-all duration-1000 ease-out',
            teamMembersVisible[2] ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-20'
          ]"
          style="transition-delay: 300ms"
        >
          <div class="bg-gradient-to-t from-black/80 via-black/30 to-transparent absolute h-full w-full z-10 rounded-xl"></div>
          <img src="../assets/images/marketing.jpg" class="absolute h-full w-full object-cover rounded-xl group-hover:scale-105 transition-transform duration-500" />
          <div class="absolute bottom-0 left-0 p-6 z-20 w-full">
            <h2 class="text-white text-2xl font-bold mb-1">Kylie Hendris</h2>
            <p class="text-violet-200 font-medium">Marketing Director</p>
            <p class="text-white/80 mt-2 text-sm">Creative strategist building powerful brands and engaging customer experiences.</p>
            <div class="flex gap-3 mt-3">
              <a href="#" class="text-white hover:text-violet-300 transition-colors">
                <Linkedin class="w-5 h-5" />
              </a>
              <a href="#" class="text-white hover:text-violet-300 transition-colors">
                <Instagram class="w-5 h-5" />
              </a>
            </div>
          </div>
        </div>
        
        <!-- Team Member 4 -->
        <div 
          :ref="el => setMemberRef(el, 3)"
          :class="[
            'min-h-[400px] border border-violet-200 relative rounded-xl shadow-lg shadow-violet-100 hover:shadow-xl hover:shadow-violet-200 transition-all duration-300 group overflow-hidden hover:cursor-pointer',
            'transform transition-all duration-1000 ease-out',
            teamMembersVisible[3] ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-20'
          ]"
          style="transition-delay: 400ms"
        >
          <div class="bg-gradient-to-t from-black/80 via-black/30 to-transparent absolute h-full w-full z-10 rounded-xl"></div>
          <img src="../assets/images/research.jpg" class="absolute h-full w-full object-cover rounded-xl group-hover:scale-105 transition-transform duration-500" />
          <div class="absolute bottom-0 left-0 p-6 z-20 w-full">
            <h2 class="text-white text-2xl font-bold mb-1">Dr. Aisha Bello</h2>
            <p class="text-violet-200 font-medium">Research Lead</p>
            <p class="text-white/80 mt-2 text-sm">Innovation driver with a PhD in Data Science and passion for cutting-edge solutions.</p>
            <div class="flex gap-3 mt-3">
              <a href="#" class="text-white hover:text-violet-300 transition-colors">
                <Linkedin class="w-5 h-5" />
              </a>
              <a href="#" class="text-white hover:text-violet-300 transition-colors">
                <Github class="w-5 h-5" />
              </a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style>
/* You can keep your existing styles or remove them since we're using inline classes */
</style>
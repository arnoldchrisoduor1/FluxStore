<script setup>
import { PackageCheck, Store, ShoppingCart, Wallet, ShieldCheck, Zap, Globe, Users } from 'lucide-vue-next';
import StatBox from '../components/StatBox.vue';
import { ref, onMounted, onUnmounted } from 'vue';

// Stat boxes with visibility refs
const statBoxes = ref([
  { title: "Orders Fulfilled", value: "1200+", icon: PackageCheck },
  { title: "Active Shops", value: "220+", icon: Store },
  { title: "Active Buyers", value: "171K+", icon: ShoppingCart },
  { title: "Transactions", value: "$320K+", icon: Wallet }
]);

// Features with visibility refs
const features = ref([
  {
    icon: ShieldCheck,
    title: "Secure Platform",
    description: "Bank-level encryption and fraud protection for all transactions"
  },
  {
    icon: Zap,
    title: "Lightning Fast",
    description: "Average checkout time under 30 seconds for returning customers"
  },
  {
    icon: Globe,
    title: "Global Reach",
    description: "Serving customers in 50+ countries worldwide"
  },
  {
    icon: Users,
    title: "Dedicated Support",
    description: "24/7 customer service with real human assistance"
  }
]);

// Refs for elements
const sectionRef = ref(null);
const headerBadgeRef = ref(null);
const headerTitleRef = ref(null);
const headerTextRef = ref(null);
const statBoxRefs = ref([]);
const featureTitleRef = ref(null);
const featureRefs = ref([]);
const testimonialRef = ref(null);

// Visibility states
const headerBadgeVisible = ref(false);
const headerTitleVisible = ref(false);
const headerTextVisible = ref(false);
const statBoxesVisible = ref(statBoxes.value.map(() => false));
const featureTitleVisible = ref(false);
const featuresVisible = ref(features.value.map(() => false));
const testimonialVisible = ref(false);

// Intersection Observer
let observer = null;

const createObserver = () => {
  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        // Header elements
        if (entry.target === headerBadgeRef.value) {
          headerBadgeVisible.value = entry.isIntersecting;
        }
        else if (entry.target === headerTitleRef.value) {
          headerTitleVisible.value = entry.isIntersecting;
        }
        else if (entry.target === headerTextRef.value) {
          headerTextVisible.value = entry.isIntersecting;
        }
        
        // Stat boxes
        else if (statBoxRefs.value.includes(entry.target)) {
          const index = statBoxRefs.value.indexOf(entry.target);
          statBoxesVisible.value[index] = entry.isIntersecting;
        }
        
        // Features title
        else if (entry.target === featureTitleRef.value) {
          featureTitleVisible.value = entry.isIntersecting;
        }
        
        // Features
        else if (featureRefs.value.includes(entry.target)) {
          const index = featureRefs.value.indexOf(entry.target);
          featuresVisible.value[index] = entry.isIntersecting;
        }
        
        // Testimonial
        else if (entry.target === testimonialRef.value) {
          testimonialVisible.value = entry.isIntersecting;
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
    headerBadgeRef.value,
    headerTitleRef.value,
    headerTextRef.value,
    featureTitleRef.value,
    testimonialRef.value,
    ...statBoxRefs.value,
    ...featureRefs.value
  ].filter(el => el);
  
  elements.forEach(el => observer.observe(el));
});

onUnmounted(() => {
  if (observer) observer.disconnect();
});
</script>

<template>
  <section id="about" ref="sectionRef">
    <div class="py-16 px-4 sm:px-6 lg:px-8 bg-gradient-to-b from-white to-indigo-50/50 w-full">
      <div class="max-w-7xl mx-auto">
        <div class="text-center flex flex-col justify-center items-center gap-5 mb-12">
          <div 
            ref="headerBadgeRef"
            :class="[
              'border border-indigo-200 px-4 py-1.5 rounded-full bg-gradient-to-r from-indigo-100 to-violet-100 shadow-sm transition-all duration-1000 ease-out',
              headerBadgeVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
            ]"
          >
            <p class="text-indigo-700 font-medium tracking-wide">Why Choose Us</p>
          </div>
          
          <h2 
            ref="headerTitleRef"
            :class="[
              'text-4xl font-bold text-indigo-900 transition-all duration-1000 ease-out delay-200',
              headerTitleVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
            ]"
          >
            What Sets Us Apart?
          </h2>
          
          <p 
            ref="headerTextRef"
            :class="[
              'text-violet-700 max-w-2xl text-lg transition-all duration-1000 ease-out delay-400',
              headerTextVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
            ]"
          >
            We're not just another marketplace - we're a community built on trust, innovation, and exceptional service.
          </p>
        </div>
        
        <!-- Stats Section -->
        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 mb-20">
          <div 
            v-for="(box, index) in statBoxes" 
            :key="box.title"
            :ref="el => statBoxRefs[index] = el"
            :class="[
              'transition-all duration-1000 ease-out',
              statBoxesVisible[index] ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
            ]"
            :style="{ transitionDelay: `${index * 100}ms` }"
          >
            <StatBox 
              :title="box.title" 
              :value="box.value" 
              :icon="box.icon"
            />
          </div>
        </div>
        
        <!-- Features Section -->
        <div class="mt-16">
          <h3 
            ref="featureTitleRef"
            :class="[
              'text-2xl font-semibold text-indigo-800 text-center mb-12 transition-all duration-1000 ease-out',
              featureTitleVisible ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
            ]"
          >
            Our Competitive Advantages
          </h3>
          
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
            <div 
              v-for="(feature, index) in features" 
              :key="feature.title"
              :ref="el => featureRefs[index] = el"
              :class="[
                'bg-white rounded-xl p-6 shadow-lg shadow-violet-100 hover:shadow-xl hover:shadow-violet-200 transition-all duration-300 border border-indigo-100/50',
                'opacity-0 translate-y-12 transition-all duration-1000 ease-out',
                featuresVisible[index] ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-12'
              ]"
              :style="{ transitionDelay: `${index * 150}ms` }"
            >
              <div class="bg-indigo-100/30 w-12 h-12 rounded-lg flex items-center justify-center mb-4">
                <component :is="feature.icon" class="h-6 w-6 text-indigo-700" />
              </div>
              <h4 class="text-lg font-bold text-indigo-900 mb-2">{{ feature.title }}</h4>
              <p class="text-indigo-700/90">{{ feature.description }}</p>
            </div>
          </div>
        </div>
        
        <!-- Testimonial Section -->
        <div 
          ref="testimonialRef"
          :class="[
            'mt-24 bg-gradient-to-r from-indigo-600 to-violet-600 rounded-2xl p-8 sm:p-12 text-white transition-all duration-1000 ease-out',
            testimonialVisible ? 'opacity-100 translate-x-0' : 'opacity-0 translate-x-12'
          ]"
        >
          <div class="max-w-4xl mx-auto">
            <div class="flex items-center gap-3 mb-4">
              <div class="w-10 h-px bg-white/50"></div>
              <span class="text-white/80 text-sm">TRUSTED BY THOUSANDS</span>
            </div>
            <p class="text-xl sm:text-2xl font-medium mb-6">
              "This platform transformed our small business. We've seen a 300% increase in sales since joining, 
              and the support team is incredibly responsive."
            </p>
            <div class="flex items-center gap-4">
              <div class="w-12 h-12 rounded-full bg-white/10 flex items-center justify-center">
                <Users class="h-6 w-6" />
              </div>
              <div>
                <p class="font-bold">Maria Rodriguez</p>
                <p class="text-white/80 text-sm">Owner, Boutique de Moda</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
<script setup>
import { PackageCheck, Store, ShoppingCart, Wallet, ShieldCheck, Zap, Globe, Users } from 'lucide-vue-next';
import StatBox from '../components/StatBox.vue';
import { ref, onMounted, onUnmounted } from 'vue';

const statBoxes = ref([
  { title: "Orders Fulfilled", value: "1200+", icon: PackageCheck, isVisible: false },
  { title: "Active Shops", value: "220+", icon: Store, isVisible: false },
  { title: "Active Buyers", value: "171K+", icon: ShoppingCart, isVisible: false },
  { title: "Transactions", value: "$320K+", icon: Wallet, isVisible: false }
]);

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

let observer;

onMounted(() => {
  observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        const index = entry.target.dataset.index;
        if (entry.target.classList.contains('statbox-container')) {
          statBoxes.value[index].isVisible = true;
        }
        observer.unobserve(entry.target);
      }
    });
  }, {
    threshold: 0.1,
    rootMargin: '0px 0px -50px 0px'
  });

  document.querySelectorAll('.statbox-container, .feature-card').forEach((el, index) => {
    el.dataset.index = index;
    observer.observe(el);
  });
});

onUnmounted(() => {
  if (observer) observer.disconnect();
});
</script>

<template>
  <div class="py-16 px-4 sm:px-6 lg:px-8 bg-gradient-to-b from-white to-indigo-50/50 w-full">
    <div class="max-w-7xl mx-auto">
      <div class="text-center flex flex-col justify-center items-center gap-5 mb-12">
        <div class="border border-indigo-200 px-4 py-1.5 rounded-full bg-gradient-to-r from-indigo-100 to-violet-100 shadow-sm">
          <p class="text-indigo-700 font-medium tracking-wide">Why Choose Us</p>
        </div>
        <h2 class="text-4xl font-bold text-indigo-900">What Sets Us Apart?</h2>
        <p class="text-violet-700 max-w-2xl text-lg">
          We're not just another marketplace - we're a community built on trust, innovation, and exceptional service.
        </p>
      </div>
      
      <!-- Stats Section -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 mb-20">
        <TransitionGroup name="fade" appear>
          <div 
            v-for="(box, index) in statBoxes" 
            :key="box.title"
            class="statbox-container"
          >
            <StatBox 
              v-show="box.isVisible"
              :title="box.title" 
              :value="box.value" 
              :icon="box.icon"
              :style="{ transitionDelay: `${index * 100}ms` }"
            />
          </div>
        </TransitionGroup>
      </div>
      
      <!-- Features Section -->
      <div class="mt-16">
        <h3 class="text-2xl font-semibold text-indigo-800 text-center mb-12">Our Competitive Advantages</h3>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div 
            v-for="(feature, index) in features" 
            :key="feature.title"
            class="feature-card bg-white rounded-xl p-6 shadow-lg shadow-violet-100 hover:shadow-xl hover:shadow-violet-200 transition-all duration-300 border border-indigo-100/50"
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
      <div class="mt-24 bg-gradient-to-r from-indigo-600 to-violet-600 rounded-2xl p-8 sm:p-12 text-white">
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
</template>

<style>
.fade-enter-from {
  opacity: 0;
  transform: translateY(20px);
}

.fade-enter-to {
  opacity: 1;
  transform: translateY(0);
}

.fade-enter-active {
  transition: all 0.5s ease;
}

.statbox-container {
  min-height: 1px;
  width: 100%;
  display: flex;
  justify-content: center;
}

.feature-card {
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.6s cubic-bezier(0.16, 1, 0.3, 1);
}

.feature-card[data-index] {
  opacity: 1;
  transform: translateY(0);
}
</style>
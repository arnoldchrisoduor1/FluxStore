<script setup>
import { Truck, ShieldPlus, Fingerprint, ReceiptEuro } from 'lucide-vue-next';
</script>

<template>
  <!-- Background Gradient -->
  <div class="bg-gradient-to-b from-white via-indigo-50 to-white h-[800px] md:h-[700px] absolute -z-20"></div>

  <!-- Hero Content -->
  <div class="relative max-w-7xl mx-auto px-6 lg:px-8 pt-24 md:pt-32 pb-20">
    <div class="grid grid-cols-1 md:grid-cols-2 gap-12 items-center">
      <!-- Left Column: Text + CTA -->
      <div class="text-center md:text-left">
        <!-- Tagline -->
         <Transition name="fadein" appear>
        <div class="inline-flex items-center gap-2 bg-indigo-100/80 px-4 py-2 rounded-full mb-6">
          <span class="text-indigo-700 font-semibold">🚀 FluxStore</span>
          <span class="text-indigo-500">| Ecommerce Simplified</span>
        </div>
        </Transition>

        <!-- Headline -->
        <Transition name="fadein" appear>
          <h1 class="text-4xl md:text-5xl lg:text-6xl font-bold leading-tight mb-6">
            <span class="bg-gradient-to-r from-indigo-600 to-violet-700 text-transparent bg-clip-text">
              Sell Smarter, Buy Easier
            </span>
          </h1>
        </Transition>

        <!-- Subheadline -->
        <Transition name="fadeinlag" appear>
          <p class="text-lg md:text-xl text-indigo-800/90 mb-8 max-w-lg mx-auto md:mx-0">
            The all-in-one platform for sellers to grow their business and buyers to shop securely.
          </p>
        </Transition>

        <!-- CTAs -->
        <Transition name="sidefadein" appear>
          <div class="flex flex-col sm:flex-row gap-4 justify-center md:justify-start mb-12">
            <button
              class="px-6 py-3.5 bg-gradient-to-r from-indigo-600 to-violet-600 text-white font-bold rounded-lg shadow-lg hover:shadow-xl transition-all hover:scale-[1.02] hover:cursor-pointer">
              Start Selling Free
            </button>
            <button
              class="px-6 py-3.5 bg-white border-2 border-indigo-200 text-indigo-700 font-bold rounded-lg hover:bg-indigo-50 transition-colors hover:cursor-pointer">
              Explore Shops
            </button>
          </div>
        </Transition>

        <!-- Trust Badges -->
         <Transition name="fadeinlag" appear>
        <div class="flex flex-wrap justify-center md:justify-start items-center gap-4 text-sm text-indigo-600">
          <div class="flex items-center gap-2">
            <Fingerprint class="w-4 h-4 text-violet-600" />
            <span>Secure Payments</span>
          </div>
          <div class="flex items-center gap-2">
            <Truck class="w-4 h-4 text-violet-600" />
            <span>Fast Delivery</span>
          </div>
        </div>
        </Transition>
      </div>

      <!-- Right Column: Spinning Orb -->
       <Transition name="sidefadein" appear>
      <div class="relative w-full h-[400px] md:h-[500px] flex justify-center items-center">
        <div
          class="w-[350px] h-[350px] md:w-[450px] md:h-[450px] rounded-full bg-white shadow-[inset_0_0_30px_theme('colors.indigo.200')] rotate-slow">
          <!-- Orb Items (Same as before) -->
          <div
            class="absolute top-[20px] left-[125px] md:left-[175px] w-[120px] h-[120px] rounded-full bg-white shadow-[inset_0_0_20px_theme('colors.indigo.300')] flex items-center justify-center">
            <div class="spin-counter text-center">
              <Truck class="h-10 w-10 mx-auto text-indigo-600" />
              <p class="font-medium mt-2 text-indigo-700 text-sm tracking-tighter">Fast Deliveries</p>
            </div>
          </div>
          <div
            class="absolute top-[120px] left-[20px] w-[120px] h-[120px] rounded-full bg-white shadow-[inset_0_0_20px_theme('colors.indigo.300')] flex items-center justify-center">
            <div class="spin-counter text-center">
              <ShieldPlus class="h-10 w-10 mx-auto text-indigo-600" />
              <p class="font-medium mt-2 text-indigo-700 text-sm tracking-tighter">Buyer Protection</p>
            </div>
          </div>
          <div
            class="absolute top-[230px] left-[125px] md:left-[175px] w-[120px] h-[120px] rounded-full bg-white shadow-[inset_0_0_20px_theme('colors.indigo.300')] flex items-center justify-center">
            <div class="spin-counter text-center">
              <Fingerprint class="h-10 w-10 mx-auto text-indigo-600" />
              <p class="font-medium mt-2 text-indigo-700 text-sm tracking-tighter">Secure Payments</p>
            </div>
          </div>
          <div
            class="absolute top-[120px] right-[20px] w-[120px] h-[120px] rounded-full bg-white shadow-[inset_0_0_20px_theme('colors.indigo.300')] flex items-center justify-center">
            <div class="spin-counter text-center">
              <ReceiptEuro class="h-10 w-10 mx-auto text-indigo-600" />
              <p class="font-medium mt-2 text-indigo-700 text-sm tracking-tighter">Easy Invoicing</p>
            </div>
          </div>
        </div>
      </div>
      </Transition>
    </div>
  </div>
</template>

<style>
/* Keep your existing animations */
@keyframes spin-reverse {
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(-360deg);
  }
}

.rotate-slow {
  animation: spin-reverse 50s linear infinite;
}

@keyframes spin-forward {
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(360deg);
  }
}

.spin-counter {
  animation: spin-forward 50s linear infinite;
}

.fadein-enter-active,
.fadein-leave-active {
  transition: opacity 1s ease;
  transition: transform 1s ease;
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
  transition: opacity 1s ease;
  transition: transform 1s ease;
}

.sidefadein-enter-from,
.sidefadein-leave-to {
  opacity: 0;
  transform: translateX(40px);
}
</style>
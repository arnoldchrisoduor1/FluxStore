<script setup>
import Navbar from "./components/Navbar.vue";
import Hero from "../src/sections/Hero.vue";
import Footer from "../src/sections/Footer.vue";
import Contact from "../src/sections/Contact.vue";
import WhyUs from "../src/sections/WhyUs.vue";
import GettingStarted from "./sections/GettingStarted.vue";
import Faq from "./sections/Faq.vue";
import Team from "./sections/Team.vue"

</script>

<template>
  <div class="overflow-hidden">
    <!-- <div class="bg-indigo-200 absolute inset-0 -z-10"></div> -->
    <div class="sticky top-2 md:top-4 z-50">
      <Navbar />
    </div>
    <main class="max-w-screen-xl mx-auto">
      <Hero />
      <WhyUs />
      <GettingStarted />
      <Team />
      <Faq />
      <Contact />
    </main>
    <Footer />
  </div>
</template>

<style scoped></style>

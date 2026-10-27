<script setup>
import Navbar from '../components/layout/Navbar.vue';
import HeroSection from '../components/sections/HeroSection.vue';
import FutsalSection from '../components/sections/FutsalSection.vue';
import FeaturesSection from '../components/sections/FeaturesSection.vue';
import Footer from '../components/layout/Footer.vue';
</script>

<template>
  <div class="min-h-screen flex flex-col bg-white text-gray-900">
    <!-- Navbar Component -->
    <Navbar />

    <!-- Main Content Area -->
    <main class="flex-grow">
      <!-- Hero Section Component with Full Animated Visual -->
      <HeroSection />

      <!-- Dedicated Futsal Section (#futsal) -->
      <FutsalSection />

      <!-- Facilities & Location Features Section (#features) -->
      <FeaturesSection />
    </main>

    <!-- Footer Component (#contact) -->
    <Footer />
  </div>
</template>

<script setup>
import Navbar from '../components/layout/Navbar.vue';
import HeroSection from '../components/sections/HeroSection.vue';
import FeaturesSection from '../components/sections/FeaturesSection.vue';
import Footer from '../components/layout/Footer.vue';
</script>

<template>
  <div class="min-h-screen flex flex-col bg-white text-gray-900">
    <!-- Navbar Component -->
    <Navbar />

    <!-- Main Content Area -->
    <main class="flex-grow">
      <!-- Hero Section Component with Full Image -->
      <HeroSection />

      <!-- Features Section -->
      <FeaturesSection />
    </main>

    <!-- Footer Component -->
    <Footer />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { Menu, X, Phone, Calendar } from '@lucide/vue';
import Button from '../ui/Button.vue';

const isMobileMenuOpen = ref(false);

const navLinks = [
  { name: 'Futsal Arena', href: '#futsal' },
  { name: 'Carwash & Detailing', href: '#carwash' },
  { name: 'Fasilitas & Kafe', href: '#features' },
  { name: 'Daftar Harga', href: '#pricing' },
  { name: 'Kontak & Lokasi', href: '#contact' },
];

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false;
};
</script>

<template>
  <header class="fixed top-0 left-0 right-0 z-50 bg-white/95 backdrop-blur-md border-b border-gray-100 transition-all">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16 sm:h-20">
        
        <!-- Brand Logo -->
        <a href="#" class="flex items-center gap-2.5 sm:gap-3 group">
          <img
            src="https://th.bing.com/th/id/OIP.UREMDPQLbngQutnBESL38AHaHh?w=108&h=108&c=1&bgcl=c41b86&r=0&o=7&dpr=2&pid=ImgRC&rm=3"
            alt="ONE STONE Logo"
            class="w-9 h-9 sm:w-10 sm:h-10 rounded-lg object-contain shrink-0 border border-gray-200 shadow-xs"
          />
          <div class="flex flex-col">
            <span class="text-lg sm:text-xl font-bold tracking-tight text-gray-900 font-['Space_Grotesk'] leading-none">
              ONE STONE
            </span>
            <span class="text-[10px] sm:text-[11px] font-medium text-gray-500 uppercase tracking-wider mt-0.5">
              Futsal & Carwash • Bali
            </span>
          </div>
        </a>

        <!-- Desktop Navigation Links -->
        <nav class="hidden md:flex items-center gap-6 lg:gap-8">
          <a
            v-for="link in navLinks"
            :key="link.name"
            :href="link.href"
            class="text-sm font-medium text-gray-600 hover:text-gray-900 transition-colors"
          >
            {{ link.name }}
          </a>
        </nav>

        <!-- Desktop Action Buttons -->
        <div class="hidden md:flex items-center gap-3 lg:gap-4">
          <a
            href="tel:+62361972566"
            class="text-sm font-medium text-gray-600 hover:text-gray-900 transition-colors px-2 py-1"
          >
            Hubungi Kami
          </a>
          <Button variant="primary" size="md" href="#booking">
            Reservasi Jadwal
          </Button>
        </div>

        <!-- Mobile Menu Button (Accessible 44x44px Tap Target) -->
        <button
          type="button"
          @click="toggleMobileMenu"
          aria-label="Buka navigasi menu"
          class="md:hidden w-11 h-11 rounded-lg text-gray-700 hover:text-gray-900 hover:bg-gray-100 flex items-center justify-center focus:outline-none focus:ring-2 focus:ring-gray-900"
        >
          <Menu v-if="!isMobileMenuOpen" class="w-6 h-6 stroke-[2]" />
          <X v-else class="w-6 h-6 stroke-[2]" />
        </button>
      </div>

      <!-- Mobile Menu Dropdown dengan Transisi Mulus & Touch Target Sempurna -->
      <transition
        enter-active-class="transition duration-200 ease-out"
        enter-from-class="opacity-0 -translate-y-2"
        enter-to-class="opacity-100 translate-y-0"
        leave-active-class="transition duration-150 ease-in"
        leave-from-class="opacity-100 translate-y-0"
        leave-to-class="opacity-0 -translate-y-2"
      >
        <div
          v-if="isMobileMenuOpen"
          class="md:hidden py-4 border-t border-gray-100 space-y-3 bg-white shadow-xl rounded-b-2xl px-2"
        >
          <nav class="flex flex-col space-y-1">
            <a
              v-for="link in navLinks"
              :key="link.name"
              :href="link.href"
              @click="closeMobileMenu"
              class="h-11 px-3.5 flex items-center text-sm font-medium text-gray-700 hover:text-gray-900 hover:bg-gray-50 rounded-lg transition-colors"
            >
              {{ link.name }}
            </a>
          </nav>

          <div class="pt-3 border-t border-gray-100 flex flex-col gap-2.5">
            <a
              href="tel:+62361972566"
              @click="closeMobileMenu"
              class="h-11 px-4 rounded-lg border border-gray-300 text-gray-800 text-sm font-medium flex items-center justify-center gap-2 hover:bg-gray-50 transition-colors"
            >
              <Phone class="w-4 h-4 text-gray-600" />
              <span>Hubungi Kami (0361 972566)</span>
            </a>
            <Button
              variant="primary"
              size="md"
              href="#booking"
              class="w-full h-11 justify-center"
              @click="closeMobileMenu"
            >
              <Calendar class="w-4 h-4 mr-2" />
              <span>Reservasi Jadwal</span>
            </Button>
          </div>
        </div>
      </transition>
    </div>
  </header>
</template>

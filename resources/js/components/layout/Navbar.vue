<script setup>
import { ref } from 'vue';
import { Menu, X, ArrowUpRight, Calendar, Phone } from '@lucide/vue';

const isMobileMenuOpen = ref(false);

// Hanya 3 link esensial (tidak terlalu banyak)
const navLinks = [
  { name: 'Futsal', href: '#futsal' },
  { name: 'Carwash', href: '#carwash' },
  { name: 'Fasilitas', href: '#features' },
];

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false;
};
</script>

<template>
  <header class="fixed top-3 sm:top-5 inset-x-0 z-50 flex flex-col items-center px-4 sm:px-6 pointer-events-none">
    <!-- Floating Transparent Capsule Bar (Unik, Simpel & Elegan) -->
    <div class="pointer-events-auto w-full max-w-3xl bg-white/50 hover:bg-white/65 backdrop-blur-md border border-white/80 shadow-[0_4px_20px_rgba(0,0,0,0.06)] rounded-full px-3.5 sm:px-5 py-2 sm:py-2.5 transition-all duration-300 flex items-center justify-between">
      
      <!-- Brand Logo & Nama -->
      <a href="#" class="flex items-center gap-2 sm:gap-2.5 group">
        <img
          src="https://th.bing.com/th/id/OIP.UREMDPQLbngQutnBESL38AHaHh?w=108&h=108&c=1&bgcl=c41b86&r=0&o=7&dpr=2&pid=ImgRC&rm=3"
          alt="ONE STONE Logo"
          class="w-7 h-7 sm:w-8 sm:h-8 rounded-full object-contain border border-white/80 shadow-xs shrink-0"
        />
        <div class="flex items-baseline gap-1.5">
          <span class="text-sm sm:text-base font-bold tracking-tight text-gray-950 font-heading leading-none">
            ONE STONE
          </span>
          <span class="hidden sm:inline text-[10px] font-medium text-gray-500 uppercase tracking-widest">
            Bali
          </span>
        </div>
      </a>

      <!-- Desktop Navigation Links (Hanya 3 Link Bersih) -->
      <nav class="hidden md:flex items-center gap-6">
        <a
          v-for="link in navLinks"
          :key="link.name"
          :href="link.href"
          class="text-xs sm:text-sm font-medium text-gray-700 hover:text-black transition-colors px-1 py-0.5"
        >
          {{ link.name }}
        </a>
      </nav>

      <!-- Desktop Action CTA -->
      <div class="hidden sm:flex items-center gap-2">
        <a
          href="tel:+62361972566"
          class="text-xs font-medium text-gray-700 hover:text-black px-2.5 py-1.5 transition-colors hidden md:inline-flex items-center gap-1"
        >
          <Phone class="w-3 h-3 text-gray-500" />
          <span>(0361) 972566</span>
        </a>
        <a
          href="#booking"
          class="inline-flex items-center gap-1 bg-gray-900 hover:bg-black text-white text-xs font-semibold px-4 py-2 rounded-full transition-all duration-150 active:scale-95 shadow-xs"
        >
          <span>Booking</span>
          <ArrowUpRight class="w-3.5 h-3.5" />
        </a>
      </div>

      <!-- Mobile Button & Hamburger Toggle -->
      <div class="flex sm:hidden items-center gap-1.5">
        <a
          href="#booking"
          class="bg-gray-900 text-white text-[11px] font-semibold px-3 py-1.5 rounded-full inline-flex items-center gap-1"
        >
          <span>Booking</span>
        </a>
        <button
          type="button"
          @click="toggleMobileMenu"
          aria-label="Menu navigasi"
          class="w-8 h-8 rounded-full bg-white/70 hover:bg-white text-gray-800 flex items-center justify-center focus:outline-none"
        >
          <Menu v-if="!isMobileMenuOpen" class="w-4 h-4 stroke-[2]" />
          <X v-else class="w-4 h-4 stroke-[2]" />
        </button>
      </div>
    </div>

    <!-- Mobile Dropdown Card (Menggantung Halus di Bawah Capsule Bar) -->
    <transition
      enter-active-class="transition duration-200 ease-out"
      enter-from-class="opacity-0 -translate-y-2 scale-95"
      enter-to-class="opacity-100 translate-y-0 scale-100"
      leave-active-class="transition duration-150 ease-in"
      leave-from-class="opacity-100 translate-y-0 scale-100"
      leave-to-class="opacity-0 -translate-y-2 scale-95"
    >
      <div
        v-if="isMobileMenuOpen"
        class="pointer-events-auto md:hidden mt-2 w-full max-w-3xl bg-white/95 backdrop-blur-lg border border-white/90 shadow-xl rounded-2xl p-4 space-y-3"
      >
        <nav class="flex flex-col space-y-1">
          <a
            v-for="link in navLinks"
            :key="link.name"
            :href="link.href"
            @click="closeMobileMenu"
            class="h-10 px-3 flex items-center text-sm font-medium text-gray-800 hover:text-black hover:bg-gray-100/70 rounded-xl transition-colors"
          >
            {{ link.name }}
          </a>
        </nav>

        <div class="pt-2 border-t border-gray-100 flex flex-col gap-2">
          <a
            href="tel:+62361972566"
            @click="closeMobileMenu"
            class="h-10 px-3.5 rounded-xl border border-gray-200 text-gray-800 text-xs font-medium flex items-center justify-center gap-2 hover:bg-gray-50"
          >
            <Phone class="w-3.5 h-3.5 text-gray-500" />
            <span>Telepon: (0361) 972566</span>
          </a>
          <a
            href="#booking"
            @click="closeMobileMenu"
            class="h-10 rounded-xl bg-gray-900 text-white text-xs font-semibold flex items-center justify-center gap-1.5"
          >
            <Calendar class="w-3.5 h-3.5" />
            <span>Reservasi Jadwal Futsal / Carwash</span>
          </a>
        </div>
      </div>
    </transition>
  </header>
</template>

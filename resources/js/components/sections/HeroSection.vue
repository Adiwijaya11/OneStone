<script setup>
import { ref } from 'vue';
import { ArrowRight, Trophy, Car, MapPin } from '@lucide/vue';
import Button from '../ui/Button.vue';

// Mode tampilan background: 'split', 'futsal', 'carwash'
const currentBg = ref('split');

const futsalImg = 'https://images.unsplash.com/photo-1574629810360-7efbbe195018?auto=format&fit=crop&w=2000&q=90';
const carwashImg = 'https://images.unsplash.com/photo-1601362840469-51e4d8d58785?auto=format&fit=crop&w=2000&q=90';

const infoItems = [
  { icon: Trophy, text: '2 Lapangan Standar FIFA' },
  { icon: Car, text: 'Cuci Hidrolik Mobil & Motor' },
  { icon: MapPin, text: 'Sebatu, Tegallalang, Bali' },
];
</script>

<template>
  <section class="relative min-h-[100svh] h-[100svh] w-full flex items-center justify-center overflow-y-auto sm:overflow-hidden bg-gray-100 select-none pt-18 sm:pt-20 pb-6 sm:pb-8">
    
    <!-- 1. LATAR BELAKANG GAMBAR (Jelas, Tajam, & Responsif) -->
    
    <!-- Opsi A: Tampilan Split (Atas-Bawah di Mobile, Kiri-Kanan di Tablet/Desktop) -->
    <div
      v-if="currentBg === 'split'"
      class="absolute inset-0 grid grid-cols-1 md:grid-cols-2 grid-rows-2 md:grid-rows-1 w-full h-full pointer-events-none"
    >
      <!-- Sisi Futsal -->
      <div class="relative w-full h-full overflow-hidden">
        <img
          :src="futsalImg"
          alt="Lapangan Futsal OneStone"
          class="w-full h-full object-cover object-center"
        />
        <div class="absolute inset-0 bg-black/15"></div>
        <div class="absolute bottom-4 left-4 md:bottom-8 md:left-8 hidden sm:flex items-center gap-2 bg-white/95 px-3 py-1.5 rounded-lg text-xs font-semibold text-gray-900 border border-gray-200 shadow-sm">
          <Trophy class="w-3.5 h-3.5 text-gray-900 shrink-0" />
          <span>Futsal Arena Standar FIFA</span>
        </div>
      </div>

      <!-- Sisi Carwash -->
      <div class="relative w-full h-full overflow-hidden border-t md:border-t-0 md:border-l border-white/40">
        <img
          :src="carwashImg"
          alt="Carwash & Detailing OneStone"
          class="w-full h-full object-cover object-center"
        />
        <div class="absolute inset-0 bg-black/15"></div>
        <div class="absolute bottom-4 right-4 md:bottom-8 md:right-8 hidden sm:flex items-center gap-2 bg-white/95 px-3 py-1.5 rounded-lg text-xs font-semibold text-gray-900 border border-gray-200 shadow-sm">
          <Car class="w-3.5 h-3.5 text-gray-900 shrink-0" />
          <span>Cuci Mobil Hidrolik & Detailing</span>
        </div>
      </div>
    </div>

    <!-- Opsi B: Full Gambar Futsal -->
    <div v-else-if="currentBg === 'futsal'" class="absolute inset-0 w-full h-full pointer-events-none">
      <img
        :src="futsalImg"
        alt="Lapangan Futsal OneStone"
        class="w-full h-full object-cover object-center"
      />
      <div class="absolute inset-0 bg-black/15"></div>
    </div>

    <!-- Opsi C: Full Gambar Carwash -->
    <div v-else class="absolute inset-0 w-full h-full pointer-events-none">
      <img
        :src="carwashImg"
        alt="Carwash OneStone"
        class="w-full h-full object-cover object-center"
      />
      <div class="absolute inset-0 bg-black/15"></div>
    </div>

    <!-- 2. KONTEN TENGAH BERSIH & PUTIH (Responsif & Proporsional di Layar HP) -->
    <div class="relative z-10 max-w-xl mx-auto px-4 sm:px-6 w-full">
      <div class="bg-white/95 backdrop-blur-md rounded-2xl p-5 sm:p-8 md:p-10 border border-gray-200/90 shadow-2xl text-center space-y-4 sm:space-y-5">
        
        <!-- Toggle Mini Latar Belakang (Responsif, Mudah Ditekan di HP) -->
        <div class="inline-flex flex-wrap items-center justify-center p-1 rounded-lg bg-gray-100 border border-gray-200 text-[11px] sm:text-xs font-medium text-gray-600 gap-1 max-w-full">
          <button
            type="button"
            @click="currentBg = 'split'"
            :class="[
              'px-2.5 sm:px-3 py-1.5 rounded-md transition-colors cursor-pointer min-h-[34px] flex items-center',
              currentBg === 'split' ? 'bg-white text-gray-900 shadow-xs font-semibold' : 'hover:text-gray-900'
            ]"
          >
            Futsal & Carwash
          </button>
          <button
            type="button"
            @click="currentBg = 'futsal'"
            :class="[
              'px-2.5 sm:px-3 py-1.5 rounded-md transition-colors cursor-pointer min-h-[34px] flex items-center',
              currentBg === 'futsal' ? 'bg-white text-gray-900 shadow-xs font-semibold' : 'hover:text-gray-900'
            ]"
          >
            Futsal Saja
          </button>
          <button
            type="button"
            @click="currentBg = 'carwash'"
            :class="[
              'px-2.5 sm:px-3 py-1.5 rounded-md transition-colors cursor-pointer min-h-[34px] flex items-center',
              currentBg === 'carwash' ? 'bg-white text-gray-900 shadow-xs font-semibold' : 'hover:text-gray-900'
            ]"
          >
            Carwash Saja
          </button>
        </div>

        <!-- Logo & Judul Perusahaan (Responsif, Proporsional di Mobile) -->
        <div class="space-y-2">
          <img
            src="https://th.bing.com/th/id/OIP.UREMDPQLbngQutnBESL38AHaHh?w=108&h=108&c=1&bgcl=c41b86&r=0&o=7&dpr=2&pid=ImgRC&rm=3"
            alt="ONE STONE Logo"
            class="w-12 h-12 sm:w-14 sm:h-14 mx-auto rounded-xl object-contain border border-gray-200/90 shadow-xs"
          />
          <div>
            <p class="text-[10px] sm:text-xs font-semibold tracking-widest text-gray-500 uppercase">
              ONE STONE • SEBATU, TEGALLALANG, BALI
            </p>
            <h1 class="text-2xl sm:text-4xl md:text-5xl font-bold tracking-tight text-gray-900 font-['Space_Grotesk'] leading-tight sm:leading-tight mt-1">
              Futsal Arena & Cuci Mobil Modern
            </h1>
          </div>
        </div>

        <!-- Deskripsi Ringkas & Mudah Dibaca -->
        <p class="text-xs sm:text-sm md:text-base text-gray-600 leading-relaxed max-w-md mx-auto">
          Fasilitas lapangan futsal berstandar kompetisi dan layanan cuci kendaraan hidrolik di Jl. Raya Bilukan, Sebatu, Tegallalang.
        </p>

        <!-- Tombol Aksi Utama (Stack Rapi di HP, Minimum 44px Touch Target) -->
        <div class="pt-1 sm:pt-2 flex flex-col sm:flex-row items-center justify-center gap-2.5 sm:gap-3 w-full">
          <Button variant="primary" size="md" href="#futsal" class="w-full sm:w-auto min-h-[44px]">
            <span>Booking Lapangan Futsal</span>
            <ArrowRight class="w-4 h-4 ml-1.5" />
          </Button>

          <Button variant="outline" size="md" href="#carwash" class="w-full sm:w-auto min-h-[44px]">
            Layanan Carwash
          </Button>
        </div>

        <!-- Info Operasional Ringkas (Auto-Wrap Bebas Tabrakan di Layar Sempit) -->
        <div class="pt-3.5 border-t border-gray-100 flex flex-wrap items-center justify-center gap-x-4 gap-y-2 text-[11px] sm:text-xs text-gray-600">
          <div
            v-for="(item, idx) in infoItems"
            :key="idx"
            class="inline-flex items-center gap-1.5"
          >
            <component :is="item.icon" class="w-3.5 h-3.5 text-gray-700 shrink-0" />
            <span>{{ item.text }}</span>
          </div>
        </div>
      </div>
    </div>

  </section>
</template>

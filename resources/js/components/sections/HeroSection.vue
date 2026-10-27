<script setup>
import { ref, onMounted, onUnmounted } from 'vue';
import { ArrowUpRight, Trophy, Car, MapPin, Clock, Phone, ChevronRight } from '@lucide/vue';

// Data slide fasilitas utama dengan foto asli berkualitas tinggi
const slides = [
  {
    id: 'futsal',
    badge: 'FASILITAS 01 • FUTSAL ARENA',
    headline: 'Arena Bertanding Kelas Utama.',
    description: 'Dua lapangan futsal rumput sintetis standar turnamen dengan pencahayaan malam LED terang dan tribun penonton di Sebatu, Tegallalang.',
    image: 'https://images.unsplash.com/photo-1574629810360-7efbbe195018?auto=format&fit=crop&w=2400&q=90',
    tag: 'Futsal FIFA Standard',
    ctaText: 'Lihat Lapangan & Booking',
    ctaRoute: '/futsal',
    ctaLink: 'https://wa.me/6281234567890?text=Halo%20One%20Stone,%20saya%20ingin%20booking%20lapangan%20futsal',
    highlights: ['Lantai Rumput Sintetis Empuk', 'Papan Skor & Rompi Lengkap', 'Penerangan Malam Terang'],
  },
  {
    id: 'carwash',
    badge: 'FASILITAS 02 • AUTO DETAILING',
    headline: 'Perawatan Mobil Bersih Total.',
    description: 'Sistem cuci hidrolik H-Track modern menjangkau kolong mobil dengan teliti, dilengkapi vakum interior wangi dan shampoo wax netral.',
    image: 'https://images.unsplash.com/photo-1601362840469-51e4d8d58785?auto=format&fit=crop&w=2400&q=90',
    tag: 'Carwash & Detailing',
    ctaText: 'Pesan Antrean Cuci',
    ctaLink: 'https://wa.me/6281234567890?text=Halo%20One%20Stone,%20saya%20ingin%20cuci%20mobil%20atau%20detailing',
    highlights: ['Cuci Kolong Hidrolik Bersih', 'Vakum Interior & Fogging', 'Shampoo Wax Ramah Cat'],
  },
];

const currentIndex = ref(0);
let timer = null;

const setSlide = (index) => {
  currentIndex.value = index;
  resetTimer();
};

const nextSlide = () => {
  currentIndex.value = (currentIndex.value + 1) % slides.length;
};

const startTimer = () => {
  timer = setInterval(nextSlide, 7000);
};

const resetTimer = () => {
  if (timer) clearInterval(timer);
  startTimer();
};

onMounted(() => {
  startTimer();
});

onUnmounted(() => {
  if (timer) clearInterval(timer);
});
</script>

<template>
  <section class="relative min-h-[100svh] h-auto lg:h-[100svh] w-full flex flex-col justify-between overflow-x-hidden bg-black text-white select-none pt-20 sm:pt-28 pb-6 sm:pb-10 px-4 sm:px-6 lg:px-12 gap-6 lg:gap-0">
    
    <!-- 1. LATAR BELAKANG GAMBAR PENUH DENGAN ANIMASI KEN BURNS & CROSSFADE HALUS -->
    <div class="absolute inset-0 w-full h-full pointer-events-none overflow-hidden">
      <div
        v-for="(slide, index) in slides"
        :key="slide.id"
        :class="[
          'absolute inset-0 w-full h-full transition-opacity duration-1000 ease-in-out',
          currentIndex === index ? 'opacity-100 z-1' : 'opacity-0 z-0'
        ]"
      >
        <img
          :src="slide.image"
          :alt="slide.headline"
          :class="[
            'w-full h-full object-cover object-center',
            currentIndex === index ? 'animate-kenburns' : ''
          ]"
        />
      </div>

      <!-- Lapisan Gradien Sinematik Gelap (Menjaga Foto Hidup & Teks Kontras Sangat Tajam) -->
      <div class="absolute inset-0 bg-gradient-to-t from-black/90 via-black/45 to-black/30 z-2"></div>
      <div class="absolute inset-0 bg-gradient-to-r from-black/80 via-black/40 to-transparent z-2 hidden lg:block"></div>
    </div>

    <!-- 2. STATUS OPERASIONAL TOP BAR -->
    <div class="relative z-10 flex items-center justify-between w-full max-w-7xl mx-auto">
      <div class="inline-flex items-center gap-2 px-3 py-1 sm:px-3.5 sm:py-1.5 rounded-full bg-black/40 backdrop-blur-md border border-white/15 text-xs text-slate-200">
        <span class="relative flex h-2 w-2">
          <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-emerald-400 opacity-75"></span>
          <span class="relative inline-flex rounded-full h-2 w-2 bg-emerald-500"></span>
        </span>
        <span class="font-medium font-body tracking-wide text-[10px] sm:text-xs">
          Buka Setiap Hari: 08.00 - 23.00 WITA &bull; Sebatu, Bali
        </span>
      </div>

      <div class="hidden sm:flex items-center gap-2 text-xs text-white/70 font-mono tracking-wider">
        <span>0{{ currentIndex + 1 }}</span>
        <span class="w-8 h-px bg-white/30"></span>
        <span>0{{ slides.length }}</span>
      </div>
    </div>

    <!-- 3. KONTEN UTAMA: TIPOGRAFI ARSITEKTURAL BOLD & MODERN -->
    <div class="relative z-10 w-full max-w-7xl mx-auto my-auto grid grid-cols-1 lg:grid-cols-12 gap-6 lg:gap-8 items-end py-4 lg:py-0">
      
      <!-- Kolom Teks Kiri -->
      <div class="lg:col-span-8 space-y-4 sm:space-y-6">
        
        <!-- Eyebrow Badge Transisi -->
        <div class="overflow-hidden">
          <p
            :key="slides[currentIndex].id"
            class="text-[11px] sm:text-sm font-bold uppercase tracking-[0.2em] sm:tracking-[0.25em] text-emerald-400 font-mono animate-in fade-in slide-in-from-bottom-2 duration-300"
          >
            {{ slides[currentIndex].badge }}
          </p>
        </div>

        <!-- Headline Utama yang Berkarakter & Menarik -->
        <h1
          :key="slides[currentIndex].id"
          class="text-3xl sm:text-5xl lg:text-7xl font-extrabold text-white font-heading leading-[1.1] sm:leading-[1.05] tracking-tight max-w-3xl drop-shadow-sm animate-in fade-in slide-in-from-bottom-3 duration-500"
        >
          {{ slides[currentIndex].headline }}
        </h1>

        <!-- Deskripsi Singkat & Bermutu -->
        <p
          :key="slides[currentIndex].id"
          class="text-xs sm:text-base lg:text-lg text-slate-200/90 font-body leading-relaxed max-w-xl font-normal drop-shadow-xs animate-in fade-in slide-in-from-bottom-4 duration-500"
        >
          {{ slides[currentIndex].description }}
        </p>

        <!-- Poin Fasilitas Cepat -->
        <div class="flex flex-wrap gap-1.5 sm:gap-2 pt-1">
          <span
            v-for="(item, idx) in slides[currentIndex].highlights"
            :key="idx"
            class="text-[10px] sm:text-xs text-white/90 bg-white/10 backdrop-blur-md px-2.5 sm:px-3 py-1 rounded-lg border border-white/15 font-body"
          >
            {{ item }}
          </span>
        </div>

        <!-- Tombol Aksi Nyata -->
        <div class="pt-2 sm:pt-3 flex flex-col sm:flex-row items-stretch sm:items-center gap-2.5 sm:gap-3">
          <router-link
            v-if="slides[currentIndex].ctaRoute"
            :to="slides[currentIndex].ctaRoute"
            class="inline-flex items-center justify-center gap-2 bg-white text-gray-950 hover:bg-slate-100 text-xs sm:text-sm font-bold px-5 sm:px-7 py-3 sm:py-3.5 rounded-full transition-all duration-200 active:scale-95 shadow-lg font-body"
          >
            <span>{{ slides[currentIndex].ctaText }}</span>
            <ArrowUpRight class="w-4 h-4" />
          </router-link>
          <a
            v-else
            :href="slides[currentIndex].ctaLink"
            target="_blank"
            rel="noopener"
            class="inline-flex items-center justify-center gap-2 bg-white text-gray-950 hover:bg-slate-100 text-xs sm:text-sm font-bold px-5 sm:px-7 py-3 sm:py-3.5 rounded-full transition-all duration-200 active:scale-95 shadow-lg font-body"
          >
            <span>{{ slides[currentIndex].ctaText }}</span>
            <ArrowUpRight class="w-4 h-4" />
          </a>

          <a
            href="tel:+62361972566"
            class="inline-flex items-center justify-center gap-2 bg-white/15 hover:bg-white/25 text-white text-xs sm:text-sm font-semibold px-5 sm:px-6 py-3 sm:py-3.5 rounded-full border border-white/20 backdrop-blur-md transition-all duration-200 active:scale-95 font-body"
          >
            <Phone class="w-4 h-4" />
            <span>Hubungi (0361) 972566</span>
          </a>
        </div>
      </div>

      <!-- Kolom Kanan: Pengendali Slide Interaktif (*Interactive Floating Cards*) -->
      <div class="lg:col-span-4 flex lg:flex-col gap-2.5 sm:gap-3 justify-end">
        <button
          v-for="(slide, index) in slides"
          :key="slide.id"
          type="button"
          @click="setSlide(index)"
          :class="[
            'text-left p-3 sm:p-4 rounded-xl sm:rounded-2xl border transition-all duration-300 backdrop-blur-md flex-1 lg:flex-none cursor-pointer group',
            currentIndex === index
              ? 'bg-white/20 border-white/50 shadow-xl scale-[1.02]'
              : 'bg-black/40 border-white/15 hover:bg-black/60 opacity-70 hover:opacity-100'
          ]"
        >
          <div class="flex items-center justify-between mb-1">
            <span class="text-[9px] sm:text-[10px] font-mono tracking-widest text-emerald-300 uppercase font-semibold">
              0{{ index + 1 }} &bull; {{ slide.tag }}
            </span>
            <ChevronRight
              :class="[
                'w-3.5 h-3.5 sm:w-4 sm:h-4 transition-transform text-white/80',
                currentIndex === index ? 'translate-x-1 text-white' : 'group-hover:translate-x-0.5'
              ]"
            />
          </div>
          <h4 class="text-xs sm:text-sm font-bold text-white font-heading truncate">
            {{ slide.headline }}
          </h4>
          
          <!-- Animated Progress Line -->
          <div class="w-full bg-white/20 h-1 rounded-full mt-2 sm:mt-2.5 overflow-hidden">
            <div
              :class="[
                'h-full bg-white transition-all',
                currentIndex === index ? 'w-full duration-7000 ease-linear' : 'w-0 duration-200'
              ]"
            ></div>
          </div>
        </button>
      </div>

    </div>

    <!-- 4. LOKASI FOOTER BARIS MINIMALIS -->
    <div class="relative z-10 w-full max-w-7xl mx-auto flex flex-col sm:flex-row items-start sm:items-center justify-between gap-2.5 sm:gap-3 text-[11px] sm:text-xs text-white/60 font-body border-t border-white/15 pt-3 sm:pt-4">
      <div class="flex items-center gap-1.5">
        <MapPin class="w-3.5 h-3.5 text-white/80 shrink-0" />
        <span>Jl. Raya Bilukan, Desa Sebatu, Kec. Tegallalang, Gianyar, Bali 80561</span>
      </div>

      <div class="flex flex-wrap items-center gap-3 sm:gap-4">
        <span class="inline-flex items-center gap-1.5">
          <Trophy class="w-3.5 h-3.5 text-white/80" />
          <span>2 Lapangan Rumput Sintetis</span>
        </span>
        <span class="hidden sm:inline">&bull;</span>
        <span class="inline-flex items-center gap-1.5">
          <Car class="w-3.5 h-3.5 text-white/80" />
          <span>Cuci Mobil & Motor Hidrolik</span>
        </span>
      </div>
    </div>

  </section>
</template>

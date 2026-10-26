<script setup>
import { ref, computed } from 'vue';
import Navbar from '../components/layout/Navbar.vue';
import Footer from '../components/layout/Footer.vue';
import {
  Trophy,
  Calendar,
  Clock,
  CheckCircle2,
  Phone,
  ArrowRight,
  ShieldCheck,
  Shirt,
  Lightbulb,
  MapPin,
  ChevronRight,
  Sparkles,
  Users,
  CircleDollarSign,
  Info,
  Maximize2
} from '@lucide/vue';

// Filter status lapangan
const activeCourtTab = ref('all'); // 'all' | 'court1' | 'court2'

// Filter jadwal ketersediaan
const selectedDate = ref('hari-ini');
const selectedCourtSchedule = ref('court1');

const dates = [
  { id: 'hari-ini', label: 'Hari Ini', subtext: '26 Oktober' },
  { id: 'besok', label: 'Besok', subtext: '27 Oktober' },
  { id: 'lusa', label: 'Lusa', subtext: '28 Oktober' },
];

// Data Lapangan
const courts = [
  {
    id: 'court1',
    name: 'Lapangan 1 (Arena Utama)',
    shortName: 'Lapangan 1',
    tag: 'Standar Turnamen',
    size: '28 × 16 Meter',
    surface: 'Monofilament 50mm',
    shortDesc: 'Rumput sintetis tebal monofilament dengan tribun penonton dan penerangan kompetisi.',
    image: 'https://images.unsplash.com/photo-1574629810360-7efbbe195018?auto=format&fit=crop&w=1000&q=80',
    status: 'Tersedia',
    facilities: [
      'Rumput Monofilament 50mm',
      '8x LED Floodlight 400W',
      'Papan Skor Digital & Tribun',
      'Gratis Bola & 2 Set Rompi',
    ],
    priceDay: 'Rp 120.000',
    priceNight: 'Rp 160.000',
    whatsappUrl: 'https://wa.me/6281234567890?text=Halo%20ONE%20STONE%20Sebatu,%20saya%20ingin%20booking%20Lapangan%201%20(Arena%20Utama)',
  },
  {
    id: 'court2',
    name: 'Lapangan 2 (Arena Standar)',
    shortName: 'Lapangan 2',
    tag: 'Sparing & Latihan',
    size: '26 × 15 Meter',
    surface: 'Synthetic Turf 45mm',
    shortDesc: 'Rumput sintetis responsif berstandar tinggi untuk sparing tim dan latihan rutin.',
    image: 'https://images.unsplash.com/photo-1529900245534-47fbf82a4d33?auto=format&fit=crop&w=1000&q=80',
    status: 'Tersedia',
    facilities: [
      'Synthetic Turf 45mm',
      '6x LED Sports Lighting',
      'Bench Tim & Scoreboard',
      'Gratis Bola & Rompi Tim',
    ],
    priceDay: 'Rp 100.000',
    priceNight: 'Rp 140.000',
    whatsappUrl: 'https://wa.me/6281234567890?text=Halo%20ONE%20STONE%20Sebatu,%20saya%20ingin%20booking%20Lapangan%202%20(Arena%20Standar)',
  },
];

// Jadwal Slot Jam Main & Ketersediaan
const scheduleSlots = [
  { time: '08.00 - 09.00', court1: 'available', court2: 'available', price1: 'Rp 120.000', price2: 'Rp 100.000' },
  { time: '09.00 - 10.00', court1: 'available', court2: 'available', price1: 'Rp 120.000', price2: 'Rp 100.000' },
  { time: '10.00 - 11.00', court1: 'booked', court2: 'available', price1: 'Rp 120.000', price2: 'Rp 100.000' },
  { time: '11.00 - 12.00', court1: 'available', court2: 'available', price1: 'Rp 120.000', price2: 'Rp 100.000' },
  { time: '13.00 - 14.00', court1: 'available', court2: 'available', price1: 'Rp 120.000', price2: 'Rp 100.000' },
  { time: '14.00 - 15.00', court1: 'available', court2: 'booked', price1: 'Rp 120.000', price2: 'Rp 100.000' },
  { time: '15.00 - 16.00', court1: 'available', court2: 'available', price1: 'Rp 160.000', price2: 'Rp 140.000' },
  { time: '16.00 - 17.00', court1: 'booked', court2: 'available', price1: 'Rp 160.000', price2: 'Rp 140.000' },
  { time: '17.00 - 18.00', court1: 'booked', court2: 'booked', price1: 'Rp 160.000', price2: 'Rp 140.000' },
  { time: '18.00 - 19.00', court1: 'booked', court2: 'available', price1: 'Rp 160.000', price2: 'Rp 140.000' },
  { time: '19.00 - 20.00', court1: 'booked', court2: 'booked', price1: 'Rp 160.000', price2: 'Rp 140.000' },
  { time: '20.00 - 21.00', court1: 'available', court2: 'booked', price1: 'Rp 160.000', price2: 'Rp 140.000' },
  { time: '21.00 - 22.00', court1: 'available', court2: 'available', price1: 'Rp 160.000', price2: 'Rp 140.000' },
  { time: '22.00 - 23.00', court1: 'available', court2: 'available', price1: 'Rp 160.000', price2: 'Rp 140.000' },
];

const filteredCourts = computed(() => {
  if (activeCourtTab.value === 'all') return courts;
  return courts.filter(c => c.id === activeCourtTab.value);
});

// Paket Tambahan / Membership
const membershipPackages = [
  {
    name: 'Paket Member Mingguan',
    subtitle: 'Solusi tim & komunitas rutin',
    discount: 'Diskon 15%',
    benefits: [
      'Kepastian jadwal jam main tetap setiap minggu',
      'Prioritas jam favorit (slot malam 19.00 - 22.00)',
      'Gratis pencucian 1 unit mobil di One Stone Carwash',
      'Penyimpanan perlengkapan tim di loker venue',
    ],
    cta: 'Gabung Member Rutin',
  },
  {
    name: 'Paket Turnamen & Sparing',
    subtitle: 'Event kompetisi atau gathering',
    discount: 'Harga Khusus',
    benefits: [
      'Penyewaan kedua lapangan sekaligus (Full Day)',
      'Fasilitas sound system & mic pembawa acara',
      'Area panggung mini & tenda peserta',
      'Koordinasi wasit berlisensi lokal Bali',
    ],
    cta: 'Konsultasi Event Turnamen',
  },
];

// Tata tertib venue
const rules = [
  { title: 'Sepatu Olahraga Khusus', desc: 'Wajib menggunakan sepatu futsal (sol karet / indoor flat atau turf TF). Dilarang menggunakan pul bola luar (metal/cleats).' },
  { title: 'Ketepatan Waktu', desc: 'Harap hadir 10-15 menit sebelum slot dimulai agar pemanasan optimal dan tidak memotong durasi pertandingan.' },
  { title: 'Kebersihan Lapangan', desc: 'Dilarang membawa makanan dan minuman manis berceceran ke atas rumput sintetis demi kenyamanan bersama.' },
  { title: 'Zona Bebas Asap Rokok', desc: 'Area dalam lapangan dan bench pemain merupakan zona dilarang merokok. Tersedia area santai khusus di luar.' },
];
</script>

<template>
  <div class="min-h-screen flex flex-col bg-white text-gray-900">
    <!-- Reusable Transparent Floating Navbar -->
    <Navbar />

    <!-- Main Content -->
    <main class="flex-grow pb-16">
      
      <!-- HERO BANNER: Foto Stadion dengan Overlay Natural (No Black BG) -->
      <section class="relative min-h-[85svh] sm:min-h-[90svh] flex flex-col justify-between overflow-hidden text-white pt-24 sm:pt-28 pb-10 sm:pb-16 px-4 sm:px-6 lg:px-8">
        
        <!-- Background Image – Gambar Penuh, Overlay Ringan & Natural -->
        <div class="absolute inset-0 w-full h-full pointer-events-none overflow-hidden">
          <img
            src="https://images.unsplash.com/photo-1574629810360-7efbbe195018?auto=format&fit=crop&w=2400&q=90"
            alt="ONE STONE Futsal Arena Sebatu"
            class="w-full h-full object-cover scale-105 animate-kenburns"
          />
          <!-- Overlay tipis – cukup untuk kontras teks, gambar tetap terlihat -->
          <div class="absolute inset-0 bg-gradient-to-t from-gray-950/90 via-gray-900/55 to-gray-800/30"></div>
          <!-- Subtle left-side darkening for text legibility -->
          <div class="absolute inset-0 bg-gradient-to-r from-gray-950/60 via-transparent to-transparent"></div>
        </div>

        <!-- Breadcrumb -->
        <div class="relative z-10 max-w-7xl mx-auto w-full">
          <nav class="inline-flex items-center gap-1.5 text-xs text-white/80 bg-black/20 backdrop-blur-md px-3.5 py-1.5 rounded-full border border-white/20">
            <router-link to="/" class="hover:text-white transition-colors">Beranda</router-link>
            <ChevronRight class="w-3 h-3 text-white/40" />
            <span class="text-white font-semibold">Arena Futsal & Lapangan</span>
          </nav>
        </div>

        <!-- Hero Content Grid -->
        <div class="relative z-10 max-w-7xl mx-auto w-full flex-grow flex items-end py-8 sm:py-10">
          <div class="w-full grid grid-cols-1 lg:grid-cols-12 gap-6 lg:gap-8 items-end">
            
            <!-- Kolom Kiri: Teks Utama -->
            <div class="lg:col-span-7 space-y-4 sm:space-y-5">
              
              <!-- Live Status Badge -->
              <div class="inline-flex items-center gap-2 px-3 py-1.5 rounded-full bg-emerald-500/25 border border-emerald-400/40 text-emerald-300 text-xs font-semibold backdrop-blur-sm">
                <span class="relative flex h-2 w-2 shrink-0">
                  <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-emerald-400 opacity-75"></span>
                  <span class="relative inline-flex rounded-full h-2 w-2 bg-emerald-500"></span>
                </span>
                <span>2 Lapangan Aktif &bull; Sebatu, Tegallalang, Gianyar</span>
              </div>

              <!-- Headline -->
              <h1 class="text-3xl xs:text-4xl sm:text-5xl lg:text-[3.5rem] xl:text-6xl font-extrabold text-white font-heading tracking-tight leading-[1.08] drop-shadow-md">
                Arena Futsal Standar Kompetisi.
              </h1>

              <!-- Deskripsi -->
              <p class="text-sm sm:text-base lg:text-lg text-white/80 font-body leading-relaxed max-w-xl">
                Dua lapangan rumput sintetis premium di Sebatu, Tegallalang. Udara pegunungan segar, penerangan LED stadium, dan fasilitas pertandingan profesional.
              </p>

              <!-- Feature Pills – Wrap rapi di mobile -->
              <div class="flex flex-wrap gap-2 pt-1">
                <span class="inline-flex items-center gap-1.5 text-xs text-white/90 bg-black/25 backdrop-blur-sm px-3 py-1.5 rounded-lg border border-white/20">
                  <Trophy class="w-3.5 h-3.5 text-emerald-400 shrink-0" />
                  <span>Monofilament 50mm</span>
                </span>
                <span class="inline-flex items-center gap-1.5 text-xs text-white/90 bg-black/25 backdrop-blur-sm px-3 py-1.5 rounded-lg border border-white/20">
                  <Lightbulb class="w-3.5 h-3.5 text-emerald-400 shrink-0" />
                  <span>LED Floodlight Stadium</span>
                </span>
                <span class="inline-flex items-center gap-1.5 text-xs text-white/90 bg-black/25 backdrop-blur-sm px-3 py-1.5 rounded-lg border border-white/20">
                  <ShieldCheck class="w-3.5 h-3.5 text-emerald-400 shrink-0" />
                  <span>Tribun & Papan Skor</span>
                </span>
                <span class="inline-flex items-center gap-1.5 text-xs text-white/90 bg-black/25 backdrop-blur-sm px-3 py-1.5 rounded-lg border border-white/20">
                  <Shirt class="w-3.5 h-3.5 text-emerald-400 shrink-0" />
                  <span>Gratis Rompi & Bola</span>
                </span>
              </div>

              <!-- CTA Buttons -->
              <div class="pt-2 flex flex-wrap gap-3">
                <a
                  href="#daftar-lapangan"
                  class="inline-flex items-center gap-2 bg-white text-gray-950 hover:bg-slate-100 text-xs sm:text-sm font-bold px-5 py-3 rounded-full transition-all duration-200 active:scale-95 shadow-lg"
                >
                  <span>Lihat Pilihan Lapangan</span>
                  <ArrowRight class="w-4 h-4" />
                </a>
                <a
                  href="#jadwal"
                  class="inline-flex items-center gap-2 bg-white/15 hover:bg-white/25 text-white text-xs sm:text-sm font-semibold px-5 py-3 rounded-full border border-white/30 backdrop-blur-sm transition-all duration-200 active:scale-95"
                >
                  <Clock class="w-4 h-4 text-emerald-400" />
                  <span>Cek Jadwal Hari Ini</span>
                </a>
              </div>
            </div>

            <!-- Kolom Kanan: Info Card – hidden di mobile kecil, muncul di lg -->
            <div class="lg:col-span-5 hidden lg:block">
              <div class="bg-white/12 border border-white/25 backdrop-blur-xl rounded-3xl p-6 space-y-4 shadow-2xl">
                <div class="flex items-center justify-between">
                  <span class="flex items-center gap-1.5 text-xs text-white/70 uppercase tracking-wider font-semibold">
                    <Clock class="w-3.5 h-3.5 text-emerald-400" />
                    Jam Operasional
                  </span>
                  <span class="bg-emerald-500/25 text-emerald-300 border border-emerald-400/35 px-2.5 py-0.5 rounded-full text-[10px] font-bold uppercase tracking-wide">
                    Setiap Hari
                  </span>
                </div>

                <div>
                  <div class="flex items-baseline gap-2">
                    <span class="text-2xl xl:text-3xl font-extrabold text-white font-heading">08.00 - 23.00</span>
                    <span class="text-xs text-white/60">WITA</span>
                  </div>
                  <p class="text-xs text-white/60 mt-1.5 leading-relaxed">
                    Booking via WhatsApp admin untuk reservasi slot harian maupun jadwal mingguan rutin.
                  </p>
                </div>

                <div class="flex items-center justify-between text-xs pt-1 border-t border-white/15">
                  <span class="text-white/60">Tarif Mulai</span>
                  <span class="font-bold text-white">Rp 100.000 <span class="text-white/50 font-normal">/ jam</span></span>
                </div>

                <a
                  href="https://wa.me/6281234567890?text=Halo%20ONE%20STONE%20Sebatu,%20saya%20ingin%20cek%20ketersediaan%20lapangan%20futsal"
                  target="_blank"
                  rel="noopener"
                  class="w-full inline-flex items-center justify-center gap-2 bg-emerald-500 hover:bg-emerald-400 text-gray-950 text-sm font-bold py-3 px-4 rounded-xl transition-all shadow-md active:scale-98"
                >
                  <Phone class="w-4 h-4" />
                  <span>WhatsApp: (0361) 972566</span>
                </a>
              </div>
            </div>

          </div>
        </div>

        <!-- Bottom Feature Bar (mobile + desktop) -->
        <div class="relative z-10 max-w-7xl mx-auto w-full pt-6 mt-auto border-t border-white/15 flex flex-col sm:flex-row items-start sm:items-center justify-between gap-2 text-xs text-white/55">
          <div class="flex items-center gap-2">
            <MapPin class="w-3.5 h-3.5 text-emerald-400 shrink-0" />
            <span>Jl. Raya Bilukan, Sebatu, Tegallalang, Gianyar, Bali</span>
          </div>
          <div class="hidden sm:flex items-center gap-3">
            <span>2 Arena Kompetisi</span>
            <span class="text-white/30">•</span>
            <span>Parkir Luas Gratis</span>
            <span class="text-white/30">•</span>
            <span>Carwash On-Site</span>
          </div>
        </div>

      </section>

      <!-- Section: Daftar Lapangan Yang Tersedia -->
      <section id="daftar-lapangan" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10 sm:py-16">
        
        <!-- Filter Tabs -->
        <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 mb-8">
          <div>
            <h2 class="text-2xl sm:text-3xl font-bold text-gray-950 font-heading tracking-tight">
              Daftar Lapangan Tersedia
            </h2>
            <p class="text-xs sm:text-sm text-gray-600 mt-1">
              Pilih spesifikasi lapangan yang sesuai dengan kebutuhan pertandingan tim Anda.
            </p>
          </div>

          <!-- Tab Selector -->
          <div class="inline-flex p-1 bg-gray-100 rounded-xl border border-gray-200/80 self-start sm:self-auto">
            <button
              type="button"
              @click="activeCourtTab = 'all'"
              :class="[
                'px-3.5 py-1.5 rounded-lg text-xs font-semibold transition-all',
                activeCourtTab === 'all'
                  ? 'bg-white text-gray-950 shadow-xs'
                  : 'text-gray-600 hover:text-gray-950'
              ]"
            >
              Semua Lapangan (2)
            </button>
            <button
              type="button"
              @click="activeCourtTab = 'court1'"
              :class="[
                'px-3.5 py-1.5 rounded-lg text-xs font-semibold transition-all',
                activeCourtTab === 'court1'
                  ? 'bg-white text-gray-950 shadow-xs'
                  : 'text-gray-600 hover:text-gray-950'
              ]"
            >
              Lapangan 1
            </button>
            <button
              type="button"
              @click="activeCourtTab = 'court2'"
              :class="[
                'px-3.5 py-1.5 rounded-lg text-xs font-semibold transition-all',
                activeCourtTab === 'court2'
                  ? 'bg-white text-gray-950 shadow-xs'
                  : 'text-gray-600 hover:text-gray-950'
              ]"
            >
              Lapangan 2
            </button>
          </div>
        </div>

        <!-- Court Cards Grid (Desain Bersih, Ringkas & Elegan) -->
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-7">
          <div
            v-for="court in filteredCourts"
            :key="court.id"
            class="group rounded-3xl border border-gray-200 bg-white overflow-hidden shadow-xs hover:shadow-xl hover:border-gray-900 transition-all duration-300 flex flex-col justify-between"
          >
            <!-- Visual Header: Foto Berkualitas & Badge Spesifikasi -->
            <div class="relative h-56 sm:h-64 w-full overflow-hidden bg-gray-950">
              <img
                :src="court.image"
                :alt="court.name"
                class="w-full h-full object-cover group-hover:scale-105 transition-transform duration-500"
                loading="lazy"
              />
              <div class="absolute inset-0 bg-gradient-to-t from-gray-950/85 via-gray-950/25 to-transparent"></div>
              
              <!-- Badges Atas: Status & Ukuran Lapangan -->
              <div class="absolute top-4 inset-x-4 flex items-center justify-between">
                <span class="inline-flex items-center gap-1.5 bg-white/95 backdrop-blur-md text-gray-950 text-xs font-bold px-3 py-1 rounded-full shadow-xs">
                  <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span>
                  <span>{{ court.status }}</span>
                </span>

                <!-- Ukuran Lapangan Highlight -->
                <span class="inline-flex items-center gap-1.5 text-xs font-semibold px-3 py-1 rounded-full bg-black/60 text-white backdrop-blur-md border border-white/20">
                  <Maximize2 class="w-3.5 h-3.5 text-emerald-400" />
                  <span>{{ court.size }}</span>
                </span>
              </div>

              <!-- Title & Kategori di Atas Gambar -->
              <div class="absolute bottom-4 inset-x-4 text-white">
                <div class="text-[11px] font-mono tracking-widest text-emerald-400 uppercase font-semibold">
                  {{ court.tag }}
                </div>
                <h3 class="text-xl sm:text-2xl font-bold font-heading tracking-tight drop-shadow-xs">
                  {{ court.name }}
                </h3>
              </div>
            </div>

            <!-- Card Body: Deskripsi Singkat, Fasilitas Inti, Tarif Sewa -->
            <div class="p-6 sm:p-7 space-y-5 flex-grow flex flex-col justify-between">
              <div class="space-y-4">
                <!-- Deskripsi Ringkas (1 Kalimat, Tidak Bertele-tele) -->
                <p class="text-xs sm:text-sm text-gray-600 font-body leading-relaxed">
                  {{ court.shortDesc }}
                </p>

                <!-- Fasilitas Utama (4 Poin Bersih & Rapi) -->
                <div class="space-y-2 pt-1">
                  <div class="text-[11px] font-bold text-gray-400 uppercase tracking-wider">
                    Fasilitas Lapangan
                  </div>
                  <div class="grid grid-cols-2 gap-2">
                    <div
                      v-for="(item, idx) in court.facilities"
                      :key="idx"
                      class="flex items-center gap-2 p-2.5 rounded-xl bg-gray-50 border border-gray-100 text-xs font-medium text-gray-800"
                    >
                      <CheckCircle2 class="w-3.5 h-3.5 text-emerald-600 shrink-0" />
                      <span class="truncate">{{ item }}</span>
                    </div>
                  </div>
                </div>

                <!-- Tarif Sewa (Siang & Malam) -->
                <div class="space-y-2 pt-1">
                  <div class="text-[11px] font-bold text-gray-400 uppercase tracking-wider">
                    Tarif Sewa Per Jam
                  </div>
                  <div class="grid grid-cols-2 gap-2.5">
                    <!-- Siang -->
                    <div class="p-3.5 rounded-2xl bg-gray-50 border border-gray-200/80">
                      <div class="text-[10px] font-semibold text-gray-500 uppercase tracking-wider">
                        Siang (08.00 - 15.00)
                      </div>
                      <div class="flex items-baseline gap-1 mt-1">
                        <span class="text-lg sm:text-xl font-extrabold text-gray-950 font-heading">
                          {{ court.priceDay }}
                        </span>
                        <span class="text-[10px] text-gray-500">/ jam</span>
                      </div>
                    </div>

                    <!-- Malam -->
                    <div class="p-3.5 rounded-2xl bg-gray-950 text-white border border-gray-950 shadow-xs">
                      <div class="text-[10px] font-semibold text-emerald-400 uppercase tracking-wider">
                        Malam (15.00 - 23.00)
                      </div>
                      <div class="flex items-baseline gap-1 mt-1">
                        <span class="text-lg sm:text-xl font-extrabold text-white font-heading">
                          {{ court.priceNight }}
                        </span>
                        <span class="text-[10px] text-gray-300">/ jam</span>
                      </div>
                    </div>
                  </div>
                </div>
              </div>

              <!-- Tombol Aksi Booking -->
              <div class="pt-4 border-t border-gray-100 mt-2">
                <a
                  :href="court.whatsappUrl"
                  target="_blank"
                  rel="noopener"
                  class="w-full py-3 px-4 rounded-xl bg-gray-950 hover:bg-black text-white text-xs sm:text-sm font-semibold flex items-center justify-center gap-2 transition-all active:scale-98 shadow-xs"
                >
                  <Phone class="w-4 h-4 text-emerald-400" />
                  <span>Booking {{ court.shortName }} via WhatsApp</span>
                  <ArrowRight class="w-4 h-4" />
                </a>
              </div>
            </div>
          </div>
        </div>

      </section>

      <!-- Section: Live Slot Matrix / Jadwal Hari Ini -->
      <section id="jadwal" class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10 sm:py-14 border-t border-gray-100">
        <div class="rounded-3xl border border-gray-200 bg-gray-50/60 p-6 sm:p-10 space-y-8">
          
          <!-- Header Jadwal -->
          <div class="flex flex-col lg:flex-row lg:items-end justify-between gap-6 pb-6 border-b border-gray-200">
            <div class="space-y-2">
              <div class="inline-flex items-center gap-1.5 text-xs font-semibold text-emerald-700 bg-emerald-50 px-2.5 py-1 rounded-full border border-emerald-200">
                <Clock class="w-3.5 h-3.5" />
                <span>Slot Waktu Real-Time</span>
              </div>
              <h2 class="text-2xl sm:text-3xl font-bold text-gray-950 font-heading tracking-tight">
                Cek Ketersediaan Slot Jadwal Main
              </h2>
              <p class="text-xs sm:text-sm text-gray-600 max-w-xl">
                Pantau ketersediaan jam main untuk hari ini dan hari berikutnya. Klik tombol booking pada slot yang Anda inginkan untuk reservasi instan.
              </p>
            </div>

            <!-- Date Selector Tabs -->
            <div class="flex items-center gap-2">
              <button
                v-for="d in dates"
                :key="d.id"
                type="button"
                @click="selectedDate = d.id"
                :class="[
                  'px-4 py-2.5 rounded-xl text-left border transition-all flex flex-col',
                  selectedDate === d.id
                    ? 'bg-gray-950 text-white border-gray-950 shadow-xs'
                    : 'bg-white text-gray-800 border-gray-200 hover:border-gray-300'
                ]"
              >
                <span class="text-xs font-bold">{{ d.label }}</span>
                <span :class="['text-[10px]', selectedDate === d.id ? 'text-gray-300' : 'text-gray-500']">{{ d.subtext }}</span>
              </button>
            </div>
          </div>

          <!-- Schedule Matrix Grid -->
          <div class="space-y-4">
            <div class="flex items-center justify-between text-xs text-gray-500">
              <div class="flex items-center gap-4">
                <span class="inline-flex items-center gap-1.5">
                  <span class="w-2.5 h-2.5 rounded-full bg-emerald-500"></span>
                  <span class="font-medium text-gray-700">Tersedia</span>
                </span>
                <span class="inline-flex items-center gap-1.5">
                  <span class="w-2.5 h-2.5 rounded-full bg-gray-400"></span>
                  <span class="font-medium text-gray-700">Terisi (Booked)</span>
                </span>
              </div>
              <span class="hidden sm:inline">Pembaruan jadwal berkala oleh admin</span>
            </div>

            <!-- Slots Grid -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-3.5">
              <div
                v-for="(slot, idx) in scheduleSlots"
                :key="idx"
                class="p-3.5 rounded-2xl bg-white border border-gray-200 shadow-2xs space-y-2.5 flex flex-col justify-between"
              >
                <div class="flex items-center justify-between">
                  <span class="text-xs font-extrabold text-gray-950 font-heading">
                    {{ slot.time }}
                  </span>
                  <span class="text-[10px] uppercase font-semibold text-gray-500">
                    WITA
                  </span>
                </div>

                <!-- Slot status per court -->
                <div class="space-y-1.5 pt-1 text-xs">
                  <!-- Lapangan 1 -->
                  <div class="flex items-center justify-between p-2 rounded-lg bg-gray-50">
                    <span class="text-[11px] font-medium text-gray-700">Lap. 1 (Utama)</span>
                    <span
                      v-if="slot.court1 === 'available'"
                      class="text-[10px] font-bold text-emerald-700 bg-emerald-100/80 px-2 py-0.5 rounded-md"
                    >
                      Tersedia
                    </span>
                    <span
                      v-else
                      class="text-[10px] font-semibold text-gray-500 bg-gray-200/80 px-2 py-0.5 rounded-md"
                    >
                      Terisi
                    </span>
                  </div>

                  <!-- Lapangan 2 -->
                  <div class="flex items-center justify-between p-2 rounded-lg bg-gray-50">
                    <span class="text-[11px] font-medium text-gray-700">Lap. 2 (Standar)</span>
                    <span
                      v-if="slot.court2 === 'available'"
                      class="text-[10px] font-bold text-emerald-700 bg-emerald-100/80 px-2 py-0.5 rounded-md"
                    >
                      Tersedia
                    </span>
                    <span
                      v-else
                      class="text-[10px] font-semibold text-gray-500 bg-gray-200/80 px-2 py-0.5 rounded-md"
                    >
                      Terisi
                    </span>
                  </div>
                </div>

                <!-- Booking CTA -->
                <a
                  :href="`https://wa.me/6281234567890?text=Halo%20ONE%20STONE,%20saya%20ingin%20booking%20jam%20${encodeURIComponent(slot.time)}%20WITA%20untuk%20tanggal%20${selectedDate}`"
                  target="_blank"
                  rel="noopener"
                  class="mt-1 w-full py-2 px-3 rounded-lg text-center text-xs font-semibold transition-colors bg-gray-100 hover:bg-gray-900 hover:text-white text-gray-800"
                >
                  Pilih Jam Ini
                </a>
              </div>
            </div>
          </div>

        </div>
      </section>

      <!-- Section: Paket Membership & Turnamen -->
      <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10 sm:py-14 border-t border-gray-100">
        <div class="max-w-3xl mb-8 space-y-2">
          <h2 class="text-2xl sm:text-3xl font-bold text-gray-950 font-heading tracking-tight">
            Paket Member Rutin & Turnamen
          </h2>
          <p class="text-xs sm:text-sm text-gray-600">
            Dapatkan keuntungan eksklusif, penghematan biaya sewa, serta kepastian slot jadwal reguler untuk komunitas Anda.
          </p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <div
            v-for="(pkg, pIdx) in membershipPackages"
            :key="pIdx"
            class="p-6 sm:p-8 rounded-3xl border border-gray-200 bg-white space-y-6 flex flex-col justify-between hover:border-gray-300 transition-colors"
          >
            <div class="space-y-4">
              <div class="flex items-center justify-between">
                <div>
                  <h3 class="text-xl font-bold text-gray-950 font-heading">
                    {{ pkg.name }}
                  </h3>
                  <p class="text-xs text-gray-500 mt-0.5">
                    {{ pkg.subtitle }}
                  </p>
                </div>
                <span class="text-xs font-extrabold px-3 py-1 rounded-full bg-emerald-100 text-emerald-800">
                  {{ pkg.discount }}
                </span>
              </div>

              <ul class="space-y-2.5 pt-2">
                <li
                  v-for="(benefit, bIdx) in pkg.benefits"
                  :key="bIdx"
                  class="flex items-start gap-2.5 text-xs sm:text-sm text-gray-700"
                >
                  <CheckCircle2 class="w-4 h-4 text-emerald-600 shrink-0 mt-0.5" />
                  <span>{{ benefit }}</span>
                </li>
              </ul>
            </div>

            <div class="pt-4 border-t border-gray-100">
              <a
                :href="`https://wa.me/6281234567890?text=Halo%20ONE%20STONE,%20saya%20tertarik%20dengan%20${encodeURIComponent(pkg.name)}`"
                target="_blank"
                rel="noopener"
                class="w-full py-2.5 px-4 rounded-xl text-xs font-bold inline-flex items-center justify-center gap-2 bg-gray-900 hover:bg-black text-white transition-all shadow-xs"
              >
                <span>{{ pkg.cta }}</span>
                <ArrowRight class="w-3.5 h-3.5" />
              </a>
            </div>
          </div>
        </div>
      </section>

      <!-- Section: Tata Tertib & Aturan Venue -->
      <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10 sm:py-14 border-t border-gray-100">
        <div class="rounded-3xl bg-gray-50 border border-gray-200 p-6 sm:p-10 space-y-6">
          <div class="flex items-center gap-2 text-xs font-bold uppercase tracking-wider text-gray-500">
            <Info class="w-4 h-4 text-gray-700" />
            <span>Tata Tertib & Ketentuan Pemakaian Lapangan</span>
          </div>

          <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-5">
            <div
              v-for="(rule, rIdx) in rules"
              :key="rIdx"
              class="bg-white p-5 rounded-2xl border border-gray-200/80 space-y-2"
            >
              <div class="text-xs font-bold text-gray-950 font-heading">
                {{ rule.title }}
              </div>
              <p class="text-xs text-gray-600 leading-relaxed font-body">
                {{ rule.desc }}
              </p>
            </div>
          </div>
        </div>
      </section>

      <!-- Section: Lokasi & Panduan Akses -->
      <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10 sm:py-14 border-t border-gray-100">
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-center">
          <div class="lg:col-span-6 space-y-4">
            <div class="inline-flex items-center gap-1.5 text-xs font-semibold text-gray-500 uppercase tracking-wider">
              <MapPin class="w-4 h-4 text-emerald-600" />
              <span>Lokasi ONE STONE Bali</span>
            </div>
            
            <h2 class="text-2xl sm:text-4xl font-bold text-gray-950 font-heading tracking-tight">
              Mudah Dijangkau di Jalur Utama Sebatu, Tegallalang.
            </h2>

            <p class="text-sm text-gray-600 font-body leading-relaxed">
              Beralamat di <strong>Jl. Raya Bilukan, Sebatu, Kec. Tegallalang, Kabupaten Gianyar, Bali 80561</strong>. Terletak di tepi jalan raya dengan area parkir mobil dan motor luas dan aman.
            </p>

            <div class="pt-2 flex flex-wrap gap-3">
              <a
                href="https://maps.google.com/?q=Jl.+Raya+Bilukan,+Sebatu,+Tegallalang,+Gianyar,+Bali"
                target="_blank"
                rel="noopener"
                class="inline-flex items-center gap-1.5 px-4 py-2.5 rounded-xl bg-gray-950 hover:bg-black text-white text-xs font-semibold transition-all shadow-xs"
              >
                <MapPin class="w-3.5 h-3.5 text-emerald-400" />
                <span>Buka Petunjuk Arah di Google Maps</span>
              </a>

              <a
                href="tel:+62361972566"
                class="inline-flex items-center gap-1.5 px-4 py-2.5 rounded-xl bg-white border border-gray-200 text-gray-800 text-xs font-semibold hover:bg-gray-50 transition-all"
              >
                <Phone class="w-3.5 h-3.5 text-gray-500" />
                <span>Telepon: (0361) 972566</span>
              </a>
            </div>
          </div>

          <div class="lg:col-span-6 rounded-3xl overflow-hidden border border-gray-200 bg-gray-100 aspect-video relative">
            <iframe
              title="Peta Lokasi ONE STONE Futsal & Carwash"
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d15783.504289895048!2d115.2936!3d-8.4358!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2dd22359be2442cf%3A0x7d6f5f3e9c687e1a!2sSebatu%2C%20Tegallalang%2C%20Gianyar%20Regency%2C%20Bali!5e0!3m2!1sen!2sid!4v1700000000000"
              class="w-full h-full border-0"
              loading="lazy"
              referrerpolicy="no-referrer-when-downgrade"
            ></iframe>
          </div>
        </div>
      </section>

    </main>

    <!-- Reusable Footer -->
    <Footer />
  </div>
</template>

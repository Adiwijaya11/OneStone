<script setup>
import { Trophy, Car, Coffee, CalendarCheck, ShieldCheck, Sparkles } from '@lucide/vue';
import Button from '../ui/Button.vue';

const services = [
  {
    icon: Trophy,
    title: 'Futsal Arena Premium',
    description:
      'Lapangan rumput sintetis dan vinyl berstandar kompetisi dengan penerangan LED terang untuk bermain nyaman siang maupun malam.',
    points: ['Lantai empuk & aman', 'Papan skor digital & tribun', 'Penyewaan rompi & bola'],
  },
  {
    icon: Car,
    title: 'Cuci Mobil Hidrolik & Detailing',
    description:
      'Teknologi lift hidrolik H-Track menjangkau kolong mobil dengan teliti menggunakan shampoo wax netral yang aman untuk cat.',
    points: ['Cuci bodi & kolong bersih', 'Vakum interior wangi', 'Paket poles & salon mobil'],
  },
  {
    icon: Coffee,
    title: 'Kafe & Ruang Tunggu Nyaman',
    description:
      'Tersedia cafe ber-AC dengan aneka minuman kopi, makanan ringan, dan Wi-Fi cepat selagi menunggu mobil Anda selesai dicuci.',
    points: ['Ruang tunggu ber-AC', 'Stopkontak & Wi-Fi kencang', 'Spot santai setelah tanding'],
  },
  {
    icon: CalendarCheck,
    title: 'Booking Jadwal Mudah',
    description:
      'Pemesanan slot lapangan futsal rutin (member) dan antrean carwash terjadwal tanpa perlu antre berlama-lama di lokasi.',
    points: ['Jadwal real-time', 'Harga transparan', 'Pilihan member bulanan hemat'],
  },
];
</script>

<template>
  <section id="features" class="bg-gray-50 py-10 sm:py-20 border-t border-gray-200">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center max-w-2xl mx-auto mb-8 sm:mb-14 space-y-2 sm:space-y-3">
        <h2 class="text-xl sm:text-3xl font-bold tracking-tight text-gray-950 font-heading">
          Fasilitas Lengkap di Satu Tempat
        </h2>
        <p class="text-xs sm:text-base text-gray-600">
          Solusi terpadu olahraga bersama teman dan perawatan kendaraan kesayangan Anda.
        </p>
      </div>

      <!-- Services Grid -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-3.5 sm:gap-6">
        <div
          v-for="(service, index) in services"
          :key="index"
          class="bg-white p-4 sm:p-6 rounded-2xl border border-gray-200/90 flex flex-col justify-between space-y-4 shadow-2xs"
        >
          <div class="space-y-2.5 sm:space-y-3">
            <div class="w-10 h-10 rounded-xl bg-gray-100 flex items-center justify-center text-gray-900">
              <component :is="service.icon" class="w-5 h-5 stroke-[1.8]" />
            </div>

            <h3 class="text-base sm:text-lg font-bold text-gray-950 font-heading">
              {{ service.title }}
            </h3>

            <p class="text-xs sm:text-sm text-gray-600 leading-relaxed">
              {{ service.description }}
            </p>
          </div>

          <!-- Bullet Points -->
          <ul class="pt-3 border-t border-gray-100 space-y-2 text-xs text-gray-700">
            <li v-for="(point, pIdx) in service.points" :key="pIdx" class="flex items-center gap-2">
              <span class="w-1.5 h-1.5 rounded-full bg-emerald-500 shrink-0"></span>
              <span>{{ point }}</span>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

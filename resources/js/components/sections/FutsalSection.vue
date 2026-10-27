<script setup>
import { Trophy, Check, Clock, Calendar, ArrowRight, ShieldCheck, Shirt, Lightbulb } from '@lucide/vue';

const specs = [
  {
    icon: Trophy,
    title: 'Rumput Sintetis Monofilament',
    description: 'Permukaan lapangan empuk dan terawat berkala, meminimalkan risiko lecet atau cedera engkel.',
  },
  {
    icon: Lightbulb,
    title: 'Penerangan LED Sorot Malam',
    description: 'Pencahayaan terang merata ke seluruh sudut lapangan untuk kenyamanan bertanding malam hari.',
  },
  {
    icon: Shirt,
    title: 'Rompi & Bola Resmi Gratis',
    description: 'Setiap penyewaan sudah termasuk peminjaman bola futsal berstandar dan dua set rompi tanding.',
  },
  {
    icon: ShieldCheck,
    title: 'Tribun & Jaring Pengaman',
    description: 'Area penonton luas di pinggir lapangan yang terlindung jaring pembatas aman dan sirkulasi udara sejuk.',
  },
];

const rates = [
  {
    period: 'Pagi - Siang',
    time: '08.00 - 15.00 WITA',
    price: 'Rp 120.000',
    unit: '/ jam',
    note: 'Cocok untuk latihan santai atau sparing pelajar.',
    featured: false,
  },
  {
    period: 'Sore - Malam',
    time: '15.00 - 23.00 WITA',
    price: 'Rp 150.000',
    unit: '/ jam',
    note: 'Waktu favorit komunitas dengan lampu LED sorot penuh.',
    featured: true,
  },
  {
    period: 'Paket Member Bulanan',
    time: 'Jadwal Rutin Mingguan',
    price: 'Diskon 15%',
    unit: '/ 4 sesi',
    note: 'Kepastian slot jam main tetap setiap minggu tanpa rebutan jadwal.',
    featured: false,
  },
];
</script>

<template>
  <section id="futsal" class="scroll-mt-20 sm:scroll-mt-24 py-12 sm:py-24 bg-white border-t border-gray-100">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      
      <!-- Section Header: Bersih, Tegas, Tanpa Hiasan Alay -->
      <div class="max-w-3xl mb-10 sm:mb-16 space-y-3">
        <div class="inline-flex items-center gap-2 text-xs uppercase tracking-widest text-gray-500 font-semibold font-body">
          <span class="w-1.5 h-1.5 rounded-full bg-emerald-600"></span>
          <span>Fasilitas Futsal One Stone</span>
        </div>

        <h2 class="text-2xl sm:text-4xl lg:text-5xl font-extrabold text-gray-950 font-heading tracking-tight leading-tight">
          Lapangan Futsal Standar Kompetisi di Tegallalang.
        </h2>

        <p class="text-sm sm:text-lg text-gray-600 font-body leading-relaxed max-w-2xl">
          Dua lapangan rumput sintetis berkualitas di Sebatu dengan udara perbukitan sejuk, pencahayaan LED malam terang, dan fasilitas tanding lengkap.
        </p>

        <div class="pt-2">
          <router-link
            to="/futsal"
            class="inline-flex items-center gap-2 px-4 sm:px-5 py-2.5 rounded-full bg-gray-950 hover:bg-black text-white text-xs font-semibold transition-all shadow-xs active:scale-98"
          >
            <span>Buka Halaman Lapangan & Cek Jadwal Lengkap</span>
            <ArrowRight class="w-3.5 h-3.5" />
          </router-link>
        </div>
      </div>

      <!-- Grid Keunggulan Fasilitas (4 Kolom Sederhana & Fungsional) -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-3.5 sm:gap-5 mb-10 sm:mb-14">
        <div
          v-for="(spec, index) in specs"
          :key="index"
          class="p-4 sm:p-6 rounded-xl sm:rounded-2xl bg-gray-50/80 border border-gray-200/80 space-y-3 flex flex-col justify-between"
        >
          <div class="space-y-2.5 sm:space-y-3">
            <div class="w-9 h-9 sm:w-10 sm:h-10 rounded-xl bg-white border border-gray-200 flex items-center justify-center text-gray-900 shadow-2xs">
              <component :is="spec.icon" class="w-4 h-4 sm:w-5 sm:h-5 stroke-[1.8]" />
            </div>

            <h3 class="text-sm sm:text-base font-bold text-gray-950 font-heading">
              {{ spec.title }}
            </h3>

            <p class="text-xs sm:text-sm text-gray-600 font-body leading-relaxed">
              {{ spec.description }}
            </p>
          </div>
        </div>
      </div>

      <!-- Blok Tarif Sewa & Booking -->
      <div class="rounded-2xl sm:rounded-3xl border border-gray-200 bg-gray-50/50 p-4 sm:p-10 lg:p-12 space-y-6 sm:space-y-8">
        <div class="flex flex-col sm:flex-row sm:items-end justify-between gap-3 sm:gap-4 border-b border-gray-200/80 pb-5 sm:pb-6">
          <div class="space-y-1">
            <h3 class="text-lg sm:text-2xl font-bold text-gray-950 font-heading">
              Daftar Tarif Sewa Lapangan
            </h3>
            <p class="text-xs sm:text-sm text-gray-600 font-body">
              Harga transparan tanpa biaya tambahan tersembunyi.
            </p>
          </div>

          <div class="text-xs text-gray-500 font-body flex items-center gap-1.5">
            <Clock class="w-3.5 h-3.5 text-gray-700 shrink-0" />
            <span>Operasional: 08.00 - 23.00 WITA</span>
          </div>
        </div>

        <!-- 3 Kartu Tarif Sederhana -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-3.5 sm:gap-5">
          <div
            v-for="(rate, rIdx) in rates"
            :key="rIdx"
            :class="[
              'p-4 sm:p-6 rounded-xl sm:rounded-2xl border transition-all flex flex-col justify-between space-y-3.5 sm:space-y-4',
              rate.featured
                ? 'bg-gray-950 text-white border-gray-950 shadow-md'
                : 'bg-white text-gray-900 border-gray-200'
            ]"
          >
            <div class="space-y-2">
              <div class="flex items-center justify-between">
                <span :class="['text-xs font-semibold uppercase tracking-wider', rate.featured ? 'text-emerald-400' : 'text-gray-500']">
                  {{ rate.period }}
                </span>
                <span v-if="rate.featured" class="text-[10px] font-bold uppercase tracking-wider bg-white/15 px-2 py-0.5 rounded-full text-white">
                  Favorit
                </span>
              </div>

              <div class="text-xs" :class="rate.featured ? 'text-gray-300' : 'text-gray-500'">
                {{ rate.time }}
              </div>

              <div class="pt-1.5 sm:pt-2 flex items-baseline gap-1">
                <span class="text-2xl sm:text-3xl font-extrabold font-heading" :class="rate.featured ? 'text-white' : 'text-gray-950'">
                  {{ rate.price }}
                </span>
                <span class="text-xs" :class="rate.featured ? 'text-gray-300' : 'text-gray-500'">
                  {{ rate.unit }}
                </span>
              </div>

              <p class="text-xs leading-relaxed pt-1.5 sm:pt-2" :class="rate.featured ? 'text-gray-300' : 'text-gray-600'">
                {{ rate.note }}
              </p>
            </div>

            <div class="pt-3.5 sm:pt-4 border-t" :class="rate.featured ? 'border-white/15' : 'border-gray-100'">
              <a
                :href="`https://wa.me/6281234567890?text=Halo%20One%20Stone%20Futsal,%20saya%20ingin%20booking%20sesi%20${encodeURIComponent(rate.period)}`"
                target="_blank"
                rel="noopener"
                :class="[
                  'w-full py-2.5 px-4 rounded-xl text-xs font-bold inline-flex items-center justify-center gap-1.5 transition-all active:scale-98',
                  rate.featured
                    ? 'bg-white text-gray-950 hover:bg-gray-100'
                    : 'bg-gray-100 text-gray-900 hover:bg-gray-200'
                ]"
              >
                <span>Cek Jadwal Sesi Ini</span>
                <ArrowRight class="w-3.5 h-3.5" />
              </a>
            </div>
          </div>
        </div>

        <!-- Catatan Tambahan & CTA Utama -->
        <div class="pt-2 sm:pt-4 flex flex-col sm:flex-row items-start sm:items-center justify-between gap-3 text-xs font-body text-gray-600">
          <div class="flex items-center gap-2">
            <Check class="w-4 h-4 text-emerald-600 shrink-0" />
            <span>Gratis parkir kendaraan roda 2 dan roda 4 di area lokasi One Stone.</span>
          </div>

          <a
            href="https://wa.me/6281234567890?text=Halo%20One%20Stone%20Futsal,%20saya%20ingin%20booking%20jadwal%20lapangan"
            target="_blank"
            rel="noopener"
            class="text-xs font-bold text-gray-950 hover:underline inline-flex items-center gap-1"
          >
            <span>Reservasi via WhatsApp Admin</span>
            <ArrowRight class="w-3.5 h-3.5" />
          </a>
        </div>
      </div>

    </div>
  </section>
</template>

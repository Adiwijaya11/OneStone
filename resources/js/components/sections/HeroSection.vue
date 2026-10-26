<script setup>
import { ref } from 'vue';
import { Trophy, Car, MapPin, Clock, ArrowRight, Phone } from '@lucide/vue';

// Tab pilihan foto showcase fasilitas nyata
const activeTab = ref('futsal');

const facilities = {
  futsal: {
    title: 'Lapangan Futsal Standar FIFA',
    desc: 'Lantai rumput sintetis empuk berkualitas dengan pencahayaan LED terang dan jaring pengaman lengkap.',
    image: 'https://images.unsplash.com/photo-1574629810360-7efbbe195018?auto=format&fit=crop&w=1800&q=85',
    tag: 'Fasilitas Futsal',
    specs: ['Rumput sintetis terawat', 'Papan skor & tribun penonton', 'Sewa rompi & bola'],
  },
  carwash: {
    title: 'Cuci Mobil Hidrolik & Detailing',
    desc: 'Layanan lift hidrolik H-Track menjangkau bagian kolong mobil secara teliti dengan shampoo pH netral.',
    image: 'https://images.unsplash.com/photo-1601362840469-51e4d8d58785?auto=format&fit=crop&w=1800&q=85',
    tag: 'Fasilitas Carwash',
    specs: ['Cuci kolong & bodi bersih', 'Vakum interior wangi', 'Cuci motor salju'],
  },
};
</script>

<template>
  <section class="min-h-[100svh] w-full bg-white text-gray-900 flex flex-col justify-center pt-24 sm:pt-28 pb-12 sm:pb-16 px-4 sm:px-6 lg:px-8 border-b border-gray-100">
    <div class="max-w-7xl mx-auto w-full">
      
      <!-- Layout Asimetris Editorial 2 Kolom (Bukan Template Slop / Bukan Kotak Mengapung) -->
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-10 lg:gap-14 items-center">
        
        <!-- Kolom Kiri: Tipografi Kuat, Bersih & Kontras Tinggi -->
        <div class="lg:col-span-6 space-y-6 sm:space-y-7">
          
          <!-- Identitas Lokasi -->
          <div class="flex items-center gap-2 text-xs uppercase tracking-widest text-gray-500 font-semibold font-body">
            <span class="w-2 h-2 rounded-full bg-emerald-600"></span>
            <span>Sebatu, Tegallalang, Gianyar - Bali</span>
          </div>

          <!-- Headline Utama (Font: Syne - Tegas & Berkarakter) -->
          <h1 class="text-4xl sm:text-5xl lg:text-6xl font-extrabold text-gray-950 font-heading leading-[1.08] tracking-tight">
            Arena Futsal & Perawatan Mobil Terpadu.
          </h1>

          <!-- Deskripsi Nyata (Font: Plus Jakarta Sans) -->
          <p class="text-base sm:text-lg text-gray-600 font-body leading-relaxed max-w-lg">
            Satu kawasan olahraga dan perawatan kendaraan di Jl. Raya Bilukan, Sebatu. Hadir dengan lapangan futsal berkualitas tinggi dan layanan cuci mobil hidrolik profesional.
          </p>

          <!-- Tombol Aksi Nyata (Tanpa Em Dash, Tanpa Style Alay) -->
          <div class="pt-2 flex flex-col sm:flex-row items-stretch sm:items-center gap-3">
            <a
              href="https://wa.me/6281234567890?text=Halo%20One%20Stone,%20saya%20ingin%20booking%20lapangan%20futsal"
              target="_blank"
              rel="noopener"
              class="inline-flex items-center justify-center gap-2 bg-gray-950 hover:bg-black text-white text-sm font-semibold px-6 py-3.5 rounded-xl transition-all duration-150 active:scale-98 shadow-sm font-body"
            >
              <span>Booking via WhatsApp</span>
              <ArrowRight class="w-4 h-4" />
            </a>

            <a
              href="#features"
              class="inline-flex items-center justify-center gap-2 bg-gray-100 hover:bg-gray-200 text-gray-900 text-sm font-semibold px-6 py-3.5 rounded-xl transition-all duration-150 active:scale-98 font-body"
            >
              <span>Lihat Fasilitas & Harga</span>
            </a>
          </div>

          <!-- Ringkasan Operasional 2 Baris Bersih -->
          <div class="pt-4 border-t border-gray-100 grid grid-cols-2 gap-4 text-xs font-body text-gray-600">
            <div class="space-y-1">
              <span class="text-gray-400 block text-[11px] uppercase tracking-wider">Jam Operasional</span>
              <span class="font-medium text-gray-900 flex items-center gap-1.5">
                <Clock class="w-3.5 h-3.5 text-gray-700 shrink-0" />
                08.00 - 23.00 WITA
              </span>
            </div>
            <div class="space-y-1">
              <span class="text-gray-400 block text-[11px] uppercase tracking-wider">Kontak Langsung</span>
              <a href="tel:+62361972566" class="font-medium text-gray-900 hover:text-black flex items-center gap-1.5">
                <Phone class="w-3.5 h-3.5 text-gray-700 shrink-0" />
                (0361) 972566
              </a>
            </div>
          </div>
        </div>

        <!-- Kolom Kanan: Showcase Fotografi Nyata Fasilitas (Jernih, Tajam, Tanpa Kabut) -->
        <div class="lg:col-span-6 space-y-4">
          
          <!-- Tab Selector Foto Nyata -->
          <div class="flex items-center gap-2 p-1 bg-gray-100 rounded-xl w-fit">
            <button
              type="button"
              @click="activeTab = 'futsal'"
              :class="[
                'px-4 py-2 rounded-lg text-xs font-semibold font-body transition-all flex items-center gap-2 cursor-pointer',
                activeTab === 'futsal'
                  ? 'bg-white text-gray-950 shadow-xs'
                  : 'text-gray-600 hover:text-gray-900'
              ]"
            >
              <Trophy class="w-3.5 h-3.5" />
              <span>Lapangan Futsal</span>
            </button>

            <button
              type="button"
              @click="activeTab = 'carwash'"
              :class="[
                'px-4 py-2 rounded-lg text-xs font-semibold font-body transition-all flex items-center gap-2 cursor-pointer',
                activeTab === 'carwash'
                  ? 'bg-white text-gray-950 shadow-xs'
                  : 'text-gray-600 hover:text-gray-900'
              ]"
            >
              <Car class="w-3.5 h-3.5" />
              <span>Cuci Mobil Hidrolik</span>
            </button>
          </div>

          <!-- Container Foto Nyata Beresolusi Tinggi -->
          <div class="relative w-full aspect-[4/3] rounded-2xl overflow-hidden border border-gray-200 bg-gray-100 shadow-md">
            <img
              :key="activeTab"
              :src="facilities[activeTab].image"
              :alt="facilities[activeTab].title"
              class="w-full h-full object-cover object-center transition-all duration-500"
            />
            
            <!-- Label Tag di Pojok Foto -->
            <div class="absolute top-4 left-4 bg-white/95 backdrop-blur-xs px-3 py-1.5 rounded-lg text-xs font-bold text-gray-900 border border-gray-200/80 shadow-xs font-body">
              {{ facilities[activeTab].tag }}
            </div>
          </div>

          <!-- Keterangan Spesifikasi di Bawah Foto -->
          <div class="bg-gray-50 rounded-xl p-4 border border-gray-200/80 space-y-2">
            <h3 class="text-sm font-bold text-gray-950 font-heading">
              {{ facilities[activeTab].title }}
            </h3>
            <p class="text-xs text-gray-600 font-body leading-relaxed">
              {{ facilities[activeTab].desc }}
            </p>
            <div class="pt-2 flex flex-wrap gap-2">
              <span
                v-for="(spec, sIdx) in facilities[activeTab].specs"
                :key="sIdx"
                class="inline-flex items-center text-[11px] font-medium text-gray-700 bg-white px-2.5 py-1 rounded-md border border-gray-200"
              >
                {{ spec }}
              </span>
            </div>
          </div>

        </div>

      </div>

    </div>
  </section>
</template>

<script setup>
import { ArrowUpRight, MapPin } from '@lucide/vue';
</script>

<template>
  <section class="relative h-[100svh] min-h-[100svh] w-full flex flex-col justify-between items-center overflow-hidden bg-gray-100 select-none px-4 sm:px-6 pt-24 pb-8">
    
    <!-- Latar Belakang Gambar Fotografi Khusus ONE STONE (Futsal & Carwash di Bali) -->
    <img
      src="/images/hero-bg.jpg"
      alt="ONE STONE Futsal Arena & Premium Auto Spa Bali"
      class="absolute inset-0 w-full h-full object-cover object-center pointer-events-none transition-transform duration-1000 scale-[1.01]"
    />

    <!-- Lapisan Lembut (Memastikan Foto Tetap Sangat Nyata, Tajam & Cerah) -->
    <div class="absolute inset-0 bg-black/10 pointer-events-none"></div>

    <!-- Spacer Atas untuk Posisi Floating Navbar -->
    <div class="relative z-10"></div>

    <!-- Konten Utama: Modern, Minimalis, dengan Card Kaca Elegan (Menjaga Keterbacaan Sempurna) -->
    <div class="relative z-10 max-w-2xl mx-auto w-full my-auto">
      <div class="bg-white/85 hover:bg-white/90 backdrop-blur-md rounded-3xl p-6 sm:p-9 md:p-10 border border-white/90 shadow-[0_12px_40px_rgba(0,0,0,0.1)] text-center space-y-5 transition-all duration-300">
        
        <!-- Label Kategori Minimalis -->
        <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-gray-100/90 border border-gray-200/80">
          <span class="w-1.5 h-1.5 rounded-full bg-emerald-500 animate-pulse"></span>
          <span class="text-[10px] sm:text-xs font-semibold tracking-widest text-gray-700 uppercase font-body">
            ONE STONE • SEBATU, BALI
          </span>
        </div>

        <!-- Heading Utama (Font: Syne - Bold & Distinctive) -->
        <h1 class="text-3xl sm:text-5xl md:text-6xl font-extrabold tracking-tight text-gray-950 font-heading leading-[1.1]">
          Futsal Arena & Cuci Mobil Modern.
        </h1>

        <!-- Deskripsi (Font: Plus Jakarta Sans - Clean & Readable) -->
        <p class="text-sm sm:text-base md:text-lg text-gray-700 font-body font-normal leading-relaxed max-w-lg mx-auto">
          Fasilitas lapangan futsal berstandar kompetisi dan layanan cuci kendaraan hidrolik di kawasan sejuk Sebatu, Tegallalang.
        </p>

        <!-- 2 Tombol Aksi Simpel & Elegan -->
        <div class="pt-2 flex flex-col sm:flex-row items-center justify-center gap-3">
          <a
            href="#futsal"
            class="w-full sm:w-auto inline-flex items-center justify-center gap-2 bg-gray-900 hover:bg-black text-white text-xs sm:text-sm font-semibold px-6 py-3 rounded-full transition-all duration-150 active:scale-95 shadow-sm font-body cursor-pointer min-h-[44px]"
          >
            <span>Booking Lapangan</span>
            <ArrowUpRight class="w-4 h-4" />
          </a>

          <a
            href="#carwash"
            class="w-full sm:w-auto inline-flex items-center justify-center gap-2 bg-white/90 hover:bg-white text-gray-900 text-xs sm:text-sm font-semibold px-6 py-3 rounded-full border border-gray-300 hover:border-gray-400 transition-all duration-150 active:scale-95 font-body cursor-pointer shadow-xs min-h-[44px]"
          >
            <span>Layanan Carwash</span>
          </a>
        </div>
      </div>
    </div>

    <!-- Bagian Bawah: Informasi Lokasi & Jam Buka Minimalis -->
    <div class="relative z-10 text-center">
      <div class="inline-flex items-center gap-1.5 px-4 py-1.5 rounded-full bg-white/80 backdrop-blur-md border border-white/90 shadow-xs text-xs text-gray-700 font-body">
        <MapPin class="w-3.5 h-3.5 text-gray-900 shrink-0" />
        <span>Jl. Raya Bilukan, Sebatu, Tegallalang, Gianyar — Bali • Buka 08:00 – 23:00 WITA</span>
      </div>
    </div>

  </section>
</template>

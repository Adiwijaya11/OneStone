<script setup>
import { MapPin, Phone, Clock, Mail } from '@lucide/vue';

const navigation = {
  futsal: [
    { name: 'Sewa Lapangan (Reguler)', href: '#' },
    { name: 'Paket Member Bulanan', href: '#' },
    { name: 'Jadwal & Turnamen', href: '#' },
    { name: 'Sewa Rompi & Bola', href: '#' },
  ],
  carwash: [
    { name: 'Cuci Mobil Hidrolik H-Track', href: '#' },
    { name: 'Cuci Motor Salju', href: '#' },
    { name: 'Vakum & Fogging Interior', href: '#' },
    { name: 'Poles Bodi & Kaca Detailing', href: '#' },
  ],
  facilities: [
    { name: 'OneStone Cafe & Wi-Fi', href: '#' },
    { name: 'Kantin & Ruang Ganti', href: '#' },
    { name: 'Mushola & Toilet Bersih', href: '#' },
    { name: 'Area Parkir Luas', href: '#' },
  ],
};
</script>

<template>
  <footer id="contact" class="bg-white border-t border-gray-200 pt-12 pb-8 sm:pt-16 sm:pb-12">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid grid-cols-2 lg:grid-cols-5 gap-8 sm:gap-10 pb-10 sm:pb-12 border-b border-gray-100">
        <!-- Brand Info -->
        <div class="col-span-2 space-y-4">
          <div class="flex items-center gap-3">
            <img
              src="https://th.bing.com/th/id/OIP.UREMDPQLbngQutnBESL38AHaHh?w=108&h=108&c=1&bgcl=c41b86&r=0&o=7&dpr=2&pid=ImgRC&rm=3"
              alt="ONE STONE Logo"
              class="w-10 h-10 rounded-lg object-contain border border-gray-200 shadow-xs shrink-0"
            />
            <div>
              <span class="text-xl font-bold tracking-tight text-gray-950 font-heading block">
                ONE STONE
              </span>
              <span class="text-xs text-gray-500 uppercase tracking-wider">Futsal & Carwash • Sebatu, Bali</span>
            </div>
          </div>

          <p class="text-sm text-gray-600 max-w-sm leading-relaxed">
            Pusat sarana olahraga futsal dan perawatan kendaraan bermotor terpadu dengan fasilitas lengkap di kawasan Sebatu, Tegallalang, Gianyar.
          </p>

          <!-- Contact details -->
          <div class="space-y-2.5 text-xs text-gray-700 pt-2">
            <div class="flex items-start gap-2">
              <MapPin class="w-4 h-4 text-gray-900 shrink-0 mt-0.5" />
              <span>Jl. Raya Bilukan, Sebatu, Kec. Tegallalang, Kabupaten Gianyar, Bali 80561</span>
            </div>
            <div class="flex items-center gap-2">
              <Clock class="w-4 h-4 text-gray-900 shrink-0" />
              <span>Buka Setiap Hari: 08.00 – 23.00 WITA</span>
            </div>
            <div class="flex items-center gap-2">
              <Phone class="w-4 h-4 text-gray-900 shrink-0" />
              <span>Telp: (0361) 972566 / WA: 0812-3456-7890</span>
            </div>
          </div>
        </div>

        <!-- Links Columns -->
        <div>
          <h3 class="text-xs font-semibold uppercase tracking-wider text-gray-900 mb-4">
            Layanan Futsal
          </h3>
          <ul class="space-y-2.5">
            <li v-for="item in navigation.futsal" :key="item.name">
              <a :href="item.href" class="text-sm text-gray-600 hover:text-gray-900 transition-colors">
                {{ item.name }}
              </a>
            </li>
          </ul>
        </div>

        <div>
          <h3 class="text-xs font-semibold uppercase tracking-wider text-gray-900 mb-4">
            Layanan Carwash
          </h3>
          <ul class="space-y-2.5">
            <li v-for="item in navigation.carwash" :key="item.name">
              <a :href="item.href" class="text-sm text-gray-600 hover:text-gray-900 transition-colors">
                {{ item.name }}
              </a>
            </li>
          </ul>
        </div>

        <div>
          <h3 class="text-xs font-semibold uppercase tracking-wider text-gray-900 mb-4">
            Fasilitas Lokasi
          </h3>
          <ul class="space-y-2.5">
            <li v-for="item in navigation.facilities" :key="item.name">
              <a :href="item.href" class="text-sm text-gray-600 hover:text-gray-900 transition-colors">
                {{ item.name }}
              </a>
            </li>
          </ul>
        </div>
      </div>

      <!-- Bottom Bar -->
      <div class="pt-8 flex flex-col sm:flex-row items-center justify-between gap-4 text-xs text-gray-500">
        <div>
          &copy; {{ new Date().getFullYear() }} OneStone Futsal & Carwash. Semua hak dilindungi undang-undang.
        </div>

        <div class="flex items-center gap-6">
          <a href="#" class="hover:text-gray-900 transition-colors">Instagram</a>
          <a href="#" class="hover:text-gray-900 transition-colors">WhatsApp</a>
          <a href="#" class="hover:text-gray-900 transition-colors">Google Maps</a>
        </div>
      </div>
    </div>
  </footer>
</template>

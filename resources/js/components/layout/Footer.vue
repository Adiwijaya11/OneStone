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
  <footer id="contact" class="bg-white border-t border-gray-200 pt-10 pb-8 sm:pt-16 sm:pb-12">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-5 gap-8 sm:gap-10 pb-8 sm:pb-12 border-b border-gray-100">
        <!-- Brand Info -->
        <div class="lg:col-span-2 space-y-4">
          <div class="flex items-center gap-3">
            <img
              src="https://th.bing.com/th/id/OIP.UREMDPQLbngQutnBESL38AHaHh?w=108&h=108&c=1&bgcl=c41b86&r=0&o=7&dpr=2&pid=ImgRC&rm=3"
              alt="ONE STONE Logo"
              class="w-9 h-9 sm:w-10 sm:h-10 rounded-lg object-contain border border-gray-200 shadow-xs shrink-0"
            />
            <div>
              <span class="text-lg sm:text-xl font-bold tracking-tight text-gray-950 font-heading block">
                ONE STONE
              </span>
              <span class="text-[11px] sm:text-xs text-gray-500 uppercase tracking-wider">Futsal & Carwash &bull; Sebatu, Bali</span>
            </div>
          </div>

          <p class="text-xs sm:text-sm text-gray-600 max-w-sm leading-relaxed">
            Pusat sarana olahraga futsal dan perawatan kendaraan bermotor terpadu dengan fasilitas lengkap di kawasan Sebatu, Tegallalang, Gianyar.
          </p>

          <!-- Contact details -->
          <div class="space-y-2 text-xs text-gray-700 pt-1">
            <div class="flex items-start gap-2">
              <MapPin class="w-4 h-4 text-gray-900 shrink-0 mt-0.5" />
              <span>Jl. Raya Bilukan, Sebatu, Kec. Tegallalang, Kabupaten Gianyar, Bali 80561</span>
            </div>
            <div class="flex items-center gap-2">
              <Clock class="w-4 h-4 text-gray-900 shrink-0" />
              <span>Buka Setiap Hari: 08.00 - 23.00 WITA</span>
            </div>
            <div class="flex items-center gap-2">
              <Phone class="w-4 h-4 text-gray-900 shrink-0" />
              <span>Telp: (0361) 972566 / WA: 0812-3456-7890</span>
            </div>
          </div>
        </div>

        <!-- Links Columns: 2 cols on mobile, 3 cols on sm+ -->
        <div class="grid grid-cols-2 sm:grid-cols-3 lg:col-span-3 gap-6 sm:gap-8">
          <div>
            <h3 class="text-xs font-semibold uppercase tracking-wider text-gray-900 mb-3 sm:mb-4">
              Layanan Futsal
            </h3>
            <ul class="space-y-2 text-xs sm:text-sm">
              <li v-for="item in navigation.futsal" :key="item.name">
                <router-link
                  v-if="item.to"
                  :to="item.to"
                  class="text-gray-600 hover:text-gray-900 transition-colors"
                >
                  {{ item.name }}
                </router-link>
                <a
                  v-else
                  :href="item.href"
                  class="text-gray-600 hover:text-gray-900 transition-colors"
                >
                  {{ item.name }}
                </a>
              </li>
            </ul>
          </div>

          <div>
            <h3 class="text-xs font-semibold uppercase tracking-wider text-gray-900 mb-3 sm:mb-4">
              Layanan Carwash
            </h3>
            <ul class="space-y-2 text-xs sm:text-sm">
              <li v-for="item in navigation.carwash" :key="item.name">
                <a :href="item.href" class="text-gray-600 hover:text-gray-900 transition-colors">
                  {{ item.name }}
                </a>
              </li>
            </ul>
          </div>

          <div class="col-span-2 sm:col-span-1">
            <h3 class="text-xs font-semibold uppercase tracking-wider text-gray-900 mb-3 sm:mb-4">
              Fasilitas Lokasi
            </h3>
            <ul class="space-y-2 text-xs sm:text-sm">
              <li v-for="item in navigation.facilities" :key="item.name">
                <a :href="item.href" class="text-gray-600 hover:text-gray-900 transition-colors">
                  {{ item.name }}
                </a>
              </li>
            </ul>
          </div>
        </div>
      </div>

      <!-- Bottom Bar -->
      <div class="pt-6 sm:pt-8 flex flex-col sm:flex-row items-center justify-between gap-3 sm:gap-4 text-xs text-gray-500">
        <div class="text-center sm:text-left">
          &copy; {{ new Date().getFullYear() }} OneStone Futsal & Carwash. Semua hak dilindungi undang-undang.
        </div>

        <div class="flex items-center gap-5 sm:gap-6">
          <a href="#" class="hover:text-gray-900 transition-colors">Instagram</a>
          <a href="https://wa.me/6281234567890" target="_blank" rel="noopener" class="hover:text-gray-900 transition-colors">WhatsApp</a>
          <a href="https://maps.google.com" target="_blank" rel="noopener" class="hover:text-gray-900 transition-colors">Google Maps</a>
        </div>
      </div>
    </div>
  </footer>
</template>

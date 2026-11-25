<script setup>
import { ref } from 'vue'

const featuredEvent = {
  badge: 'EVENT TAHUNAN TERBESAR',
  title: 'Festival Layang-Layang Bukik Ponggang',
  date: 'Agustus 2026 • 09.00 WIB - Selesai',
  location: 'Area Puncak Utama, Bukik Ponggang',
  description:
    'Saksikan ratusan layang-layang hias dan tradisional mengudara di langit Sijunjung. Dilengkapi dengan bazar kuliner UMKM lokal, pertunjukan kesenian Minangkabau, dan hadiah total jutaan rupiah.',
  highlights: [
    'Kategori Layang-layang Kreasi & Tradisional',
    'Bazar Kuliner & Kerajinan Nagari',
    'Hiburan Musik & Kesenian Daerah'
  ],
  image: '/img/hero/hero-4.jpg'
}

const upcomingEvents = ref([
  {
    id: 1,
    category: 'Komunitas',
    title: 'Sunset Camp & Akustik Malam',
    date: 'Setiap Sabtu - Minggu',
    time: '16.00 WIB - Selesai',
    desc: 'Nikmati suasana malam dari ketinggian dengan api unggun, musik akustik lokal, dan pemandangan bintang.'
  },
  {
    id: 2,
    category: 'Budaya',
    title: 'Pentas Seni & Randai Nagari',
    date: 'Minggu Pekan ke-2',
    time: '14.00 - 17.00 WIB',
    desc: 'Penampilan silat tradisi, randai, dan musik talempong dari sanggar seni pemuda setempat.'
  },
  {
    id: 3,
    category: 'Olahraga',
    title: 'Fun Trail & Gowes Puncak',
    date: 'Minggu Pekan ke-4',
    time: '07.00 - 11.00 WIB',
    desc: 'Jalur menantang dengan panorama perbukitan hijau yang cocok untuk komunitas sepeda dan lari lintas alam.'
  }
])
</script>

<template>
  <section id="event" class="py-20 bg-slate-50">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Header Section -->
      <div class="text-center max-w-2xl mx-auto mb-14">
        <span class="text-xs font-bold tracking-widest uppercase text-emerald-700">
          Agenda & Kegiatan
        </span>
        <h2 class="mt-2 text-3xl sm:text-4xl font-extrabold text-slate-900">
          Kemeriahan di Puncak Bukik Ponggang
        </h2>
        <p class="mt-3 text-slate-600 text-sm sm:text-base">
          Temukan berbagai festival budaya, kompetisi, hingga kegiatan akhir pekan yang seru untuk keluarga dan komunitas.
        </p>
      </div>

      <!-- Featured Event Card -->
      <div class="bg-white rounded-2xl shadow-sm border border-slate-200/80 overflow-hidden mb-10">
        <div class="grid grid-cols-1 lg:grid-cols-12">
          <!-- Gambar Highlight -->
          <div class="lg:col-span-5 relative min-h-260px bg-emerald-900">
            <img
              :src="featuredEvent.image"
              :alt="featuredEvent.title"
              class="w-full h-full object-cover opacity-90"
            />
            <span class="absolute top-4 left-4 bg-yellow-400 text-slate-900 text-xs font-extrabold px-3 py-1.5 rounded-full shadow">
              {{ featuredEvent.badge }}
            </span>
          </div>

          <!-- Detail Highlight -->
          <div class="lg:col-span-7 p-6 sm:p-8 lg:p-10 flex flex-col justify-between">
            <div>
              <div class="flex flex-wrap items-center gap-4 text-xs font-medium text-emerald-700 mb-3">
                <span class="bg-emerald-50 px-3 py-1 rounded-full">
                  📅 {{ featuredEvent.date }}
                </span>
                <span class="bg-emerald-50 px-3 py-1 rounded-full">
                  📍 {{ featuredEvent.location }}
                </span>
              </div>

              <h3 class="text-2xl font-bold text-slate-900 mb-3">
                {{ featuredEvent.title }}
              </h3>
              <p class="text-slate-600 text-sm leading-relaxed mb-6">
                {{ featuredEvent.description }}
              </p>

              <!-- Poin Kegiatan -->
              <ul class="space-y-2 mb-8">
                <li
                  v-for="(item, idx) in featuredEvent.highlights"
                  :key="idx"
                  class="flex items-center gap-2.5 text-sm text-slate-700"
                >
                  <span class="w-5 h-5 rounded-full bg-emerald-100 text-emerald-700 flex items-center justify-center text-xs font-bold">
                    ✓
                  </span>
                  {{ item }}
                </li>
              </ul>
            </div>

            <div class="flex flex-wrap gap-3">
              <a
                href="#lokasi"
                class="inline-flex items-center justify-center px-6 py-2.5 rounded-full bg-emerald-700 hover:bg-emerald-800 text-white text-sm font-semibold transition"
              >
                Info & Kunjungan
              </a>
              <a
                href="#galeri"
                class="inline-flex items-center justify-center px-6 py-2.5 rounded-full border border-slate-300 hover:bg-slate-100 text-slate-700 text-sm font-semibold transition"
              >
                Lihat Dokumentasi
              </a>
            </div>
          </div>
        </div>
      </div>

      <!-- Grid Agenda Rutin -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
        <div
          v-for="event in upcomingEvents"
          :key="event.id"
          class="bg-white rounded-xl p-6 border border-slate-200/80 shadow-sm hover:shadow-md transition flex flex-col justify-between"
        >
          <div>
            <div class="flex items-center justify-between mb-4">
              <span class="text-xs font-semibold px-2.5 py-1 rounded-md bg-emerald-50 text-emerald-700">
                {{ event.category }}
              </span>
              <span class="text-xs text-slate-500 font-medium">
                {{ event.date }}
              </span>
            </div>

            <h4 class="text-lg font-bold text-slate-900 mb-2">
              {{ event.title }}
            </h4>
            <p class="text-sm text-slate-600 leading-relaxed mb-4">
              {{ event.desc }}
            </p>
          </div>

          <div class="pt-4 border-t border-slate-100 flex items-center justify-between text-xs text-slate-500">
            <span>🕒 {{ event.time }}</span>
            <span class="text-emerald-700 font-semibold">Terbuka untuk Umum</span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
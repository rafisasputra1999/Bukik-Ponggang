<script setup>
import { ref, computed } from "vue";

const DATA_GALERI = [
  // === KATEGORI: PANORAMA (5 Foto) ===
  {
    id: 1,
    judul: "Panorama Senja dari Puncak",
    deskripsi: "Pemandangan 360 derajat perbukitan hijau menjelang matahari terbenam.",
    kategori: "Panorama",
    badge: "Spot Favorit",
    gambar: "/img/hero/hero-1.jpg",
    tampilDiSemua: true, // Muncul saat default (Semua Momen)
  },
  {
    id: 2,
    judul: "Udara Segar Pagi Hari",
    deskripsi: "Hamparan hijau berkabut tipis di kawasan Bukit Ponggang.",
    kategori: "Panorama",
    gambar: "/img/hero/hero-3.jpg",
    tampilDiSemua: true,
  },
  {
    id: 3,
    judul: "Gardu Pandang Utama",
    deskripsi: "Spot foto ikonik berlatar lembah dan perbukitan.",
    kategori: "Panorama",
    gambar: "/img/hero/hero-2.jpg",
    tampilDiSemua: true,
  },
  {
    id: 4,
    judul: "Area Bersantai Keluarga",
    deskripsi: "Area rumput luas yang nyaman untuk piknik akhir pekan.",
    kategori: "Panorama",
    gambar: "/img/hero/hero-1.jpg",
    tampilDiSemua: false, // Hidden saat default, muncul saat klik "Panorama"
  },
  {
    id: 5,
    judul: "Jalur Setapak Puncak",
    deskripsi: "Akses jalan kaki santai menuju titik tertinggi bukit.",
    kategori: "Panorama",
    gambar: "/img/hero/hero-3.jpg",
    tampilDiSemua: false, // Hidden saat default, muncul saat klik "Panorama"
  },

  // === KATEGORI: FESTIVAL LAYANG (5 Foto) ===
  {
    id: 6,
    judul: "Kemeriahan Festival Layang-layang",
    deskripsi: "Ratusan layang-layang hias menghiasi langit biru Bukit Ponggang.",
    kategori: "Festival Layang",
    badge: "Event Tahunan",
    gambar: "/img/hero/hero-4.jpg",
    tampilDiSemua: true, // Muncul saat default (Semua Momen)
  },
  {
    id: 7,
    judul: "Layang-layang Tradisional",
    deskripsi: "Karya kreatif peserta lokal dari berbagai komunitas.",
    kategori: "Festival Layang",
    gambar: "/img/hero/hero-5.jpg",
    tampilDiSemua: true,
  },
  {
    id: 8,
    judul: "Antusiasme Pengunjung Festival",
    deskripsi: "Keluarga dan wisatawan berkumpul menyaksikan atraksi udara.",
    kategori: "Festival Layang",
    gambar: "/img/about.jpg",
    tampilDiSemua: false, // Hidden saat default, muncul saat klik "Festival Layang"
  },
  {
    id: 9,
    judul: "Persiapan Penerbangan Layangan",
    deskripsi: "Momen kebersamaan tim sebelum menerbangkan layangan raksasa.",
    kategori: "Festival Layang",
    gambar: "/img/hero/hero-1.jpg",
    tampilDiSemua: false,
  },
  {
    id: 10,
    judul: "Siluet Layang-layang Senja",
    deskripsi: "Penutupan festival diiringi cahaya matahari sore.",
    kategori: "Festival Layang",
    gambar: "/img/hero/hero-3.jpg",
    tampilDiSemua: false,
  },
];

const KATEGORI_LIST = ["Semua Momen", "Panorama", "Festival Layang"];

const kategoriAktif = ref("Semua Momen");
const fotoTerpilih = ref(null);

// Otomatis menyaring data dan mengambil tepat 5 foto untuk Bento Grid
const galeriTampil = computed(() => {
  const hasilFilter =
    kategoriAktif.value === "Semua Momen"
      ? DATA_GALERI.filter((item) => item.tampilDiSemua)
      : DATA_GALERI.filter((item) => item.kategori === kategoriAktif.value);

  return hasilFilter.slice(0, 5);
});
</script>

<template>
  <section id="galeri" class="py-16 lg:py-24 bg-surface-alt">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      
      <!-- Header & Tombol Filter -->
      <div class="flex flex-col md:flex-row md:items-end justify-between mb-10 gap-4">
        <div>
          <span class="inline-block px-3 py-1 text-xs font-semibold tracking-wider uppercase rounded-full bg-ponggang-50 text-ponggang-700 border border-ponggang-100 mb-3">
            Galeri Momen
          </span>
          <h2 class="text-3xl sm:text-4xl font-bold text-slate-800">
            Keindahan di Setiap Sudut Bukit
          </h2>
        </div>

        <!-- Filter Pills Interaktif -->
        <div class="flex flex-wrap gap-2">
          <button
            v-for="kategori in KATEGORI_LIST"
            :key="kategori"
            @click="kategoriAktif = kategori"
            :class="[
              'px-4 py-2 rounded-full text-sm font-medium transition cursor-pointer',
              kategoriAktif === kategori
                ? 'bg-ponggang-700 text-white shadow-sm'
                : 'bg-white text-slate-600 hover:bg-ponggang-50 hover:text-ponggang-700 border border-slate-200'
            ]"
          >
            {{ kategori }}
          </button>
        </div>
      </div>

      <!-- Bento Grid (Selalu 5 Gambar & Layout Konsisten) -->
      <div class="grid grid-cols-1 md:grid-cols-4 md:grid-rows-2 gap-4 md:h-520px">
        <div
          v-for="(item, index) in galeriTampil"
          :key="item.id"
          @click="fotoTerpilih = item"
          :class="[
            'group relative rounded-2xl overflow-hidden shadow-sm cursor-pointer',
            index === 0 ? 'md:col-span-2 md:row-span-2 min-h-300px' : 'min-h-240px'
          ]"
        >
          <img
            :src="item.gambar"
            :alt="item.judul"
            class="w-full h-full object-cover transition duration-500 group-hover:scale-105"
          />

          <!-- Overlay Gelap -->
          <div
            :class="[
              'absolute inset-0 bg-linear-to-t from-black/75 via-black/20 to-transparent transition duration-300',
              index === 0
                ? 'opacity-85 group-hover:opacity-95'
                : 'opacity-0 group-hover:opacity-100'
            ]"
          />

          <!-- Teks Caption -->
          <div
            :class="[
              'absolute bottom-0 left-0 text-white transition duration-300',
              index === 0
                ? 'p-6'
                : 'p-4 translate-y-2 group-hover:translate-y-0 opacity-0 group-hover:opacity-100'
            ]"
          >
            <span
              v-if="item.badge"
              class="inline-block px-2.5 py-1 text-xs font-medium bg-ponggang-500 rounded-md mb-2"
            >
              {{ item.badge }}
            </span>
            <h3 :class="index === 0 ? 'text-xl font-bold' : 'font-semibold text-base'">
              {{ item.judul }}
            </h3>
            <p :class="index === 0 ? 'text-sm text-slate-200 mt-1' : 'text-xs text-slate-200'">
              {{ item.deskripsi }}
            </p>
          </div>
        </div>
      </div>
    </div>

    <!-- Popup Lightbox (Teleport ke body agar tidak terpotong parent) -->
    <Teleport to="body">
      <div
        v-if="fotoTerpilih"
        @click="fotoTerpilih = null"
        class="fixed inset-0 z-50 bg-black/80 backdrop-blur-sm flex items-center justify-center p-4"
      >
        <div
          @click.stop
          class="relative max-w-4xl w-full bg-white rounded-2xl overflow-hidden shadow-2xl"
        >
          <button
            @click="fotoTerpilih = null"
            aria-label="Tutup pratinjau"
            class="absolute top-3 right-3 z-10 w-9 h-9 rounded-full bg-black/60 hover:bg-black text-white flex items-center justify-center transition cursor-pointer"
          >
            ✕
          </button>

          <img
            :src="fotoTerpilih.gambar"
            :alt="fotoTerpilih.judul"
            class="w-full max-h-[75vh] object-cover"
          />

          <div class="p-5 bg-white">
            <span class="text-xs font-semibold text-ponggang-600 uppercase tracking-wider">
              {{ fotoTerpilih.kategori }}
            </span>
            <h3 class="text-lg font-bold text-slate-800">{{ fotoTerpilih.judul }}</h3>
            <p class="text-sm text-slate-500">{{ fotoTerpilih.deskripsi }}</p>
          </div>
        </div>
      </div>
    </Teleport>
  </section>
</template>

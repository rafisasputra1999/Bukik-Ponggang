<script setup>
const locationInfo = {
  badge: 'LOKASI & AKSES',
  title: 'Temukan Jalan Menuju Puncak',
  subtitle:
    'Akses mudah dijangkau dari pusat Kabupaten Sijunjung dengan jalur yang ramah kendaraan roda dua maupun roda empat.',
  address: 'Kawasan Wisata Bukik Ponggang, Kec. Kupitan, Kabupaten Sijunjung, Sumatera Barat',
  hours: 'Setiap Hari • 07.00 - 18.00 WIB',
  ticket: 'Rp 5.000 - Rp 10.000 / orang (Parkir terpisah)',
  mapsLink: 'https://maps.google.com/?q=Bukik+Ponggang+Sijunjung',
  whatsappLink:
    'https://wa.me/6281266185783?text=Halo%20pengelola%20Bukik%20Ponggang,%20saya%20ingin%20bertanya%20informasi%20kunjungan.'
}

const facilities = [
  'Area Parkir Luas',
  'Mushola & Toilet Bersih',
  'Warung Kuliner Lokal',
  'Gardu Pandang & Spot Foto',
  'Area Camping Ground',
  'Gazebo Istirahat'
]
</script>

<template>
  <section id="lokasi" class="py-20 bg-white">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Header Section -->
      <div class="text-center max-w-2xl mx-auto mb-14">
        <span class="inline-block text-xs font-bold tracking-widest uppercase text-emerald-700 bg-emerald-50 px-3 py-1 rounded-full">
          {{ locationInfo.badge }}
        </span>
        <h2 class="mt-3 text-3xl sm:text-4xl font-extrabold text-slate-900">
          {{ locationInfo.title }}
        </h2>
        <p class="mt-3 text-slate-600 text-sm sm:text-base">
          {{ locationInfo.subtitle }}
        </p>
      </div>

      <!-- Konten Utama: Peta & Detail Informasi -->
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-stretch">
        <!-- Kolom Kiri: Google Maps Embed -->
        <div class="lg:col-span-7 rounded-2xl overflow-hidden border border-slate-200 shadow-sm min-h-360px lg:min-h-460px bg-slate-100">
          <iframe
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3989.484487851925!2d100.83057027406025!3d-0.7411880352714139!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x2e2b250076e8ca65%3A0xecfe85a689a3cf0c!2sbukik%20ponggang!5e0!3m2!1sen!2sid!4v1795625866241!5m2!1sen!2sid"
            class="w-full h-full min-h-360px lg:min-h-460px border-0"
            allowfullscreen=""
            loading="lazy"
            referrerpolicy="strict-origin-when-cross-origin"
            title="Peta Lokasi Bukik Ponggang"
          ></iframe>
        </div>

        <!-- Kolom Kanan: Kartu Info Kunjungan -->
        <div class="lg:col-span-5 bg-slate-50 rounded-2xl p-6 sm:p-8 border border-slate-200/80 flex flex-col justify-between">
          <div class="space-y-6">
            <h3 class="text-xl font-bold text-slate-900">
              Informasi Kunjungan
            </h3>

            <!-- Alamat -->
            <div class="flex items-start gap-3.5">
              <div class="w-10 h-10 rounded-xl bg-emerald-100 text-emerald-700 flex items-center justify-center shrink-0 font-bold">
                📍
              </div>
              <div>
                <p class="text-xs font-semibold uppercase tracking-wider text-slate-400">
                  Alamat
                </p>
                <p class="text-sm font-medium text-slate-800 mt-0.5 leading-relaxed">
                  {{ locationInfo.address }}
                </p>
              </div>
            </div>

            <!-- Jam Operasional -->
            <div class="flex items-start gap-3.5">
              <div class="w-10 h-10 rounded-xl bg-emerald-100 text-emerald-700 flex items-center justify-center shrink-0 font-bold">
                🕒
              </div>
              <div>
                <p class="text-xs font-semibold uppercase tracking-wider text-slate-400">
                  Jam Operasional
                </p>
                <p class="text-sm font-medium text-slate-800 mt-0.5">
                  {{ locationInfo.hours }}
                </p>
              </div>
            </div>

            <!-- Tiket Masuk -->
            <div class="flex items-start gap-3.5">
              <div class="w-10 h-10 rounded-xl bg-emerald-100 text-emerald-700 flex items-center justify-center shrink-0 font-bold">
                🎟️
              </div>
              <div>
                <p class="text-xs font-semibold uppercase tracking-wider text-slate-400">
                  Estimasi Tiket Masuk
                </p>
                <p class="text-sm font-medium text-slate-800 mt-0.5">
                  {{ locationInfo.ticket }}
                </p>
              </div>
            </div>

            <!-- Fasilitas Tersedia -->
            <div class="pt-4 border-t border-slate-200/80">
              <p class="text-xs font-semibold uppercase tracking-wider text-slate-400 mb-3">
                Fasilitas Wisata
              </p>
              <div class="flex flex-wrap gap-2">
                <span
                  v-for="(item, idx) in facilities"
                  :key="idx"
                  class="text-xs font-medium bg-white border border-slate-200 text-slate-700 px-3 py-1.5 rounded-lg"
                >
                  ✓ {{ item }}
                </span>
              </div>
            </div>
          </div>

          <!-- Tombol Aksi -->
          <div class="mt-8 pt-6 border-t border-slate-200/80 flex flex-col sm:flex-row gap-3">
            <a
              :href="locationInfo.mapsLink"
              target="_blank"
              rel="noopener noreferrer"
              class="flex-1 inline-flex items-center justify-center px-5 py-3 rounded-full bg-emerald-700 hover:bg-emerald-800 text-white text-sm font-semibold transition shadow-sm"
            >
              Buka Google Maps
            </a>
            <a
              :href="locationInfo.whatsappLink"
              target="_blank"
              rel="noopener noreferrer"
              class="flex-1 inline-flex items-center justify-center px-5 py-3 rounded-full bg-yellow-400 hover:bg-yellow-500 text-slate-900 text-sm font-bold transition shadow-sm"
            >
              Hubungi Pengelola
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
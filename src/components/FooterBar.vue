<script setup>
const currentYear = new Date().getFullYear();

const quickLinks = [
  { name: "Beranda", href: "#" },
  { name: "Tentang Kami", href: "#tentang" },
  { name: "Agenda & Event", href: "#event" },
  { name: "Galeri Wisata", href: "#galeri" },
  { name: "Lokasi & Tiket", href: "#lokasi" },
];
</script>

<template>
  <footer class="bg-slate-900 text-slate-300 border-t border-slate-800">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <!-- Kolom 1: Brand & Deskripsi SEO -->
        <div>
          <h3 class="text-white text-xl font-bold tracking-tight">
            Bukik Ponggang
          </h3>
          <p class="mt-3 text-sm text-slate-400 leading-relaxed">
            Destinasi wisata alam perbukitan di Kec. Kupitan, Kabupaten
            Sijunjung, Sumatera Barat. Nikmati panorama alam, Sunset Camp,
            kesenian daerah, dan Festival Layang-Layang.
          </p>
        </div>

        <!-- Kolom 2: Navigasi Cepat -->
        <div>
          <h4 class="text-white text-sm font-semibold uppercase tracking-wider">
            Navigasi
          </h4>
          <ul class="mt-3 space-y-2 text-sm">
            <li v-for="link in quickLinks" :key="link.name">
              <a
                :href="link.href"
                class="hover:text-emerald-400 transition-colors"
              >
                {{ link.name }}
              </a>
            </li>
          </ul>
        </div>

        <!-- Kolom 3: Informasi Kunjungan & Kontak -->
        <div>
          <h4 class="text-white text-sm font-semibold uppercase tracking-wider">
            Informasi & Kontak
          </h4>
          <ul class="mt-3 space-y-2 text-sm text-slate-400">
            <li>
              <strong class="text-slate-200">Alamat:</strong> Kec. Kupitan, Kab.
              Sijunjung, Sumatera Barat
            </li>
            <li>
              <strong class="text-slate-200">Jam Buka:</strong> Setiap Hari
              (07.00 – 18.00 WIB)
            </li>
            <li>
              <strong class="text-slate-200">Tiket Masuk:</strong> Rp 5.000 – Rp
              10.000 / orang
            </li>
            <li class="pt-1">
              <a
                href= "https://wa.me/6281266185783?text=Halo%20pengelola%20Bukik%20Ponggang,%20saya%20ingin%20bertanya%20informasi%20kunjungan."
                target="_blank"
                rel="noopener noreferrer"
                class="inline-flex items-center text-emerald-400 hover:text-emerald-300 font-medium"
              >
                Hubungi Pengelola (si Ad Dali) &rarr;
              </a>
            </li>
          </ul>
        </div>
      </div>

      <!-- Bottom Copyright & Kredit Developer -->
      <div
        class="mt-10 pt-6 border-t border-slate-800 flex flex-col sm:flex-row justify-between items-center text-xs text-slate-500 gap-4"
      >
        <p>
          &copy; {{ currentYear }} Kawasan Wisata Bukik Ponggang Sijunjung. Hak
          Cipta Dilindungi.
        </p>
        <p>
          Dikembangkan oleh
          <span class="text-slate-300 font-medium">Rafi Sasputra</span>
        </p>
      </div>
    </div>
  </footer>
</template>

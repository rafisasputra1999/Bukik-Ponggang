<template>
  <section id="tentang" class="py-16 lg:py-24 bg-surface-main">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
      
      <!-- Kolom Kiri: Gambar -->
      <div class="relative">
        <div class="aspect-4/3 rounded-2xl overflow-hidden shadow-lg">
          <img 
            src="/img/about.jpg" 
            alt="Pemandangan Alam Bukit Ponggang" 
            class="w-full h-full object-cover"
            loading="lazy"
          />
        </div>
        <!-- Floating Badge -->
        <div class="absolute -bottom-6 -right-4 sm:right-6 bg-ponggang-700 text-white p-5 rounded-xl shadow-md">
          <p class="text-2xl font-bold">Destinasi Alam</p>
          <p class="text-sm text-ponggang-100">Wisata Keluarga & Budaya</p>
        </div>
      </div>

      <!-- Kolom Kanan: Teks Tentang Kami -->
      <div>
        <span class="inline-block px-3 py-1 text-xs font-semibold tracking-wider uppercase rounded-full bg-ponggang-50 text-ponggang-700 border border-ponggang-100 mb-4">
          Tentang Bukit Ponggang
        </span>
        
        <h2 class="text-3xl sm:text-4xl font-bold text-slate-800 leading-tight mb-6">
          Menyatu dengan Alam, Merayakan Budaya di Puncak Ketinggian
        </h2>
        
        <p class="text-slate-600 leading-relaxed mb-4">
          Bukit Ponggang hadir sebagai destinasi wisata alam yang menawarkan ketenangan jauh dari hiruk-pikuk perkotaan. Dari ketinggian bukit, pengunjung disuguhi panorama hijau yang memanjakan mata, embusan angin sejuk, serta pemandangan langit terbuka yang memukau.
        </p>
        
        <p class="text-slate-600 leading-relaxed mb-8">
          Lebih dari sekadar tempat bersantai, kawasan ini menjadi ruang berkumpul bagi keluarga dan komunitas—mulai dari kemeriahan <strong>Festival Layang-layang</strong>, piknik akhir pekan, hingga beragam spot foto alam yang berkesan.
        </p>

        <!-- Poin Keunggulan Singkat -->
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 mb-8">
          <div class="flex items-start gap-3">
            <div class="w-8 h-8 rounded-lg bg-ponggang-50 text-ponggang-600 flex items-center justify-center shrink-0 font-bold">✓</div>
            <div>
              <h3 class="font-semibold text-slate-800">Panorama Asri</h3>
              <p class="text-sm text-slate-500">Pemandangan bukit hijau & angin sejuk alami.</p>
            </div>
          </div>
          <div class="flex items-start gap-3">
            <div class="w-8 h-8 rounded-lg bg-ponggang-50 text-ponggang-600 flex items-center justify-center shrink-0 font-bold">✓</div>
            <div>
              <h3 class="font-semibold text-slate-800">Event & Budaya</h3>
              <p class="text-sm text-slate-500">Ruang kreatif untuk festival dan aktivitas warga.</p>
            </div>
          </div>
        </div>

        <a href="https://www.instagram.com/bukik_ponggang/" class="inline-flex items-center px-6 py-3 rounded-lg bg-ponggang-500 hover:bg-ponggang-600 text-white font-medium transition">
          Lihat Lebih Banyak
        </a>
      </div>

    </div>
  </div>
</section>

</template>
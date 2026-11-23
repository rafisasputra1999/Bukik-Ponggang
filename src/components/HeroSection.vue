<script setup>
import { ref, watch } from 'vue'
import emblaCarouselVue from 'embla-carousel-vue'
import Autoplay from 'embla-carousel-autoplay'

const slides = [
  {
    img: '/img/hero/hero-1.jpg',
    alt: 'Pemandangan perbukitan Bukik Ponggang',
    title: 'Bukik Ponggang',
    text: 'Wisata alam di Kabupaten Sijunjung.',
  },
  {
    img: '/img/hero/hero-2.jpg',
    alt: 'Matahari terbenam dari puncak bukit',
    title: 'Sunset Terbaik',
    text: 'Nikmati senja dari ketinggian.',
  },
  {
    img: '/img/hero/hero-3.jpg',
    alt: 'Festival Layang di Bukik Ponggang',
    title: 'Festival Layang',
    text: 'Event tahunan yang meriah.',
  },
  {
    img: '/img/hero/hero-4.jpg',
    alt: 'Festival Layang di Bukik Ponggang',
    title: 'Festival Layang',
    text: 'Event tahunan yang meriah.',
  },
  {
    img: '/img/hero/hero-5.jpg',
    alt: 'Festival Layang di Bukik Ponggang',
    title: 'Festival Layang',
    text: 'Event tahunan yang meriah.',
  },
]

const [emblaRef, emblaApi] = emblaCarouselVue({ loop: true }, [
  Autoplay({ delay: 4000, stopOnInteraction: false }),
])

const selected = ref(0)

watch(emblaApi, (api) => {
  if (!api) return
  selected.value = api.selectedScrollSnap()
  api.on('select', () => {
    selected.value = api.selectedScrollSnap()
  })
})

const prev = () => emblaApi.value?.scrollPrev()
const next = () => emblaApi.value?.scrollNext()
const goTo = (i) => emblaApi.value?.scrollTo(i)
</script>

<template>
  <section class="relative">
    <div class="overflow-hidden" ref="emblaRef">
      <div class="flex">
        <div
          v-for="(slide, i) in slides"
          :key="slide.img"
          class="relative min-w-0 flex-[0_0_100%]"
        >
          <img
            :src="slide.img"
            :alt="slide.alt"
            class="h-[70vh] lg:h-screen w-full object-cover"
            :loading="i === 0 ? 'eager' : 'lazy'"
          />
          <div class="absolute inset-0 flex flex-col items-center justify-center bg-black/40 px-4 text-center text-white">
            <h1 v-if="i === 0" class="text-4xl font-bold md:text-6xl">{{ slide.title }}</h1>
            <h2 v-else class="text-4xl font-bold md:text-6xl">{{ slide.title }}</h2>
            <p class="mt-3 max-w-xl md:text-lg">{{ slide.text }}</p>
            <a href="#lokasi" class="mt-6 rounded-full bg-green-600 px-6 py-3 font-semibold hover:bg-green-700">
              Lihat Lokasi
            </a>
          </div>
        </div>
      </div>
    </div>

    <!-- tombol panah -->
    <button @click="prev" aria-label="Slide sebelumnya"
      class="absolute left-3 top-1/2 -translate-y-1/2 rounded-full bg-black/50 px-3 py-2 text-white hover:bg-black/70">
      &lsaquo;
    </button>
    <button @click="next" aria-label="Slide berikutnya"
      class="absolute right-3 top-1/2 -translate-y-1/2 rounded-full bg-black/50 px-3 py-2 text-white hover:bg-black/70">
      &rsaquo;
    </button>

    <!-- titik indikator -->
    <div class="absolute bottom-4 left-1/2 flex -translate-x-1/2 gap-2">
      <button
        v-for="(slide, i) in slides"
        :key="slide.img"
        @click="goTo(i)"
        :aria-label="`Ke slide ${i + 1}`"
        class="h-3 w-3 rounded-full"
        :class="i === selected ? 'bg-white' : 'bg-white/50'"
      />
    </div>
  </section>
</template>
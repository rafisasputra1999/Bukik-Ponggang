<script setup>
import { ref } from 'vue'
import { onClickOutside } from '@vueuse/core'

const open = ref(false)
const navRef = ref(null)

const links = [
  { label: 'Tentang', href: '#tentang' },
  { label: 'Event', href: '#event' },
  { label: 'Galeri', href: '#galeri' },
  { label: 'Lokasi', href: '#lokasi' },
]

const close = () => (open.value = false)

onClickOutside(navRef, close)
</script>

<template>
  <header
    ref="navRef"
    class="sticky top-0 z-50 bg-ponggang-700 text-surface-main"
    @keydown.esc.window="close"
  >
    <nav class="mx-auto flex max-w-6xl items-center justify-between px-6 py-4">
      <a href="#" class="text-xl font-bold">Bukik <span class="italic text-amber-300">Ponggang</span></a>

      <!-- menu desktop: tersembunyi di layar kecil -->
      <ul class="hidden gap-6 md:flex">
        <li v-for="link in links" :key="link.href">
          <a :href="link.href" class="hover:underline hover:text-amber-300">{{ link.label }}</a>
        </li>
      </ul>

      <!-- tombol hamburger: hanya tampil di layar kecil -->
      <button
        @click="open = !open"
        class="md:hidden"
        :aria-label="open ? 'Tutup menu' : 'Buka menu'"
        :aria-expanded="open"
      >
        <svg v-if="!open" class="h-7 w-7" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
          <path stroke-linecap="round" d="M4 6h16M4 12h16M4 18h16" />
        </svg>
        <svg v-else class="h-7 w-7" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
          <path stroke-linecap="round" d="M6 6l12 12M18 6L6 18" />
        </svg>
      </button>
    </nav>

    <!-- menu mobile: muncul kalau open = true -->
    <Transition
      enter-active-class="transition duration-300 ease-out"
      enter-from-class="transform -translate-y-4 opacity-0"
      enter-to-class="transform translate-y-0 opacity-100"
      leave-active-class="transition duration-200 ease-in"
      leave-from-class="transform translate-y-0 opacity-100"
      leave-to-class="transform -translate-y-4 opacity-0"
    >
      <ul v-if="open" class="border-t border-green-700 px-6 pb-4 md:hidden text-right">
        <li v-for="link in links" :key="link.href">
          <a :href="link.href" @click="close" class="block py-3 hover:underline hover:text-amber-300">
            {{ link.label }}
          </a>
        </li>
      </ul>
    </Transition>
  </header>
</template>
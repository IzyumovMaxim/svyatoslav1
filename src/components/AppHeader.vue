<script setup lang="ts">
import { onMounted, onUnmounted, ref } from 'vue'
import { navLinks, site } from '../data/site'

const menuOpen = ref(false)
const headerBorder = ref(false)

function closeMenu() {
  menuOpen.value = false
}

function onScroll() {
  headerBorder.value = window.scrollY > 10
}

onMounted(() => {
  window.addEventListener('scroll', onScroll, { passive: true })
})

onUnmounted(() => {
  window.removeEventListener('scroll', onScroll)
})
</script>

<template>
  <header
    class="fixed inset-x-0 top-0 z-50 border-b bg-brand-950/80 backdrop-blur-md transition-colors"
    :class="headerBorder ? 'border-slate-800/60' : 'border-transparent'"
  >
    <div class="mx-auto flex max-w-6xl items-center justify-between px-4 py-4 sm:px-6">
      <a href="#" class="flex items-center gap-2.5" @click="closeMenu">
        <img :src="site.logo" :alt="site.title" class="h-9 w-auto" />
        <span class="text-lg font-bold text-white">
          Волга<span class="text-accent-400">НефтеСтрой</span>
        </span>
      </a>

      <nav class="hidden items-center gap-8 md:flex" aria-label="Основная навигация">
        <a v-for="link in navLinks" :key="link.href" :href="link.href" class="nav-link">
          {{ link.label }}
        </a>
        <a :href="site.phoneHref" class="btn-primary py-2 text-sm">Позвонить</a>
      </nav>

      <button
        type="button"
        class="flex h-10 w-10 items-center justify-center rounded-lg border border-slate-700 text-slate-300 md:hidden"
        :aria-expanded="menuOpen"
        aria-label="Открыть меню"
        @click="menuOpen = !menuOpen"
      >
        <svg v-if="!menuOpen" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
          <path stroke-linecap="round" d="M4 7h16M4 12h16M4 17h16" />
        </svg>
        <svg v-else class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
          <path stroke-linecap="round" d="M6 6l12 12M18 6L6 18" />
        </svg>
      </button>
    </div>

    <nav
      v-show="menuOpen"
      class="border-t border-slate-800 bg-brand-950 px-4 py-4 md:hidden"
      aria-label="Мобильная навигация"
    >
      <div class="flex flex-col gap-1">
        <a
          v-for="link in navLinks"
          :key="link.href"
          :href="link.href"
          class="rounded-lg px-3 py-2.5 text-slate-300 hover:bg-slate-800 hover:text-white"
          @click="closeMenu"
        >
          {{ link.label }}
        </a>
        <a
          :href="site.phoneHref"
          class="mt-2 rounded-xl bg-accent-500 px-3 py-2.5 text-center font-semibold text-white hover:bg-accent-400"
          @click="closeMenu"
        >
          Позвонить
        </a>
      </div>
    </nav>
  </header>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { navLinks, site } from '../data/site'
import AppIcon from './AppIcon.vue'

const menuOpen = ref(false)

function closeMenu() {
  menuOpen.value = false
}
</script>

<template>
  <div class="hidden bg-navy-950 text-xs text-slate-300 md:block">
    <div class="container-x flex items-center justify-between py-2">
      <span class="flex items-center gap-2">
        <AppIcon name="pin" class="h-4 w-4 text-accent-500" />
        {{ site.base }} · {{ site.geography }}
      </span>
      <div class="flex items-center gap-6">
        <a :href="`mailto:${site.email}`" class="flex items-center gap-2 hover:text-white">
          <AppIcon name="mail" class="h-4 w-4 text-accent-500" />
          {{ site.email }}
        </a>
        <a :href="site.phoneHref" class="flex items-center gap-2 font-semibold text-white hover:text-accent-500">
          <AppIcon name="phone" class="h-4 w-4 text-accent-500" />
          {{ site.phone }}
        </a>
      </div>
    </div>
  </div>

  <header class="sticky top-0 z-50 border-b-2 border-accent-500 bg-navy-800 shadow-lg shadow-navy-950/20">
    <div class="container-x flex items-center justify-between gap-4 py-3">
      <a href="#" class="flex shrink-0 items-center gap-2.5" @click="closeMenu">
        <img :src="site.logo" alt="Логотип ООО «ВолгаНефтеСтрой»" class="h-10 w-auto" width="40" height="40" />
        <span class="text-base font-extrabold uppercase leading-tight tracking-wide text-white sm:text-lg">
          Волга<span class="text-accent-500">НефтеСтрой</span>
        </span>
      </a>

      <nav class="hidden items-center gap-5 whitespace-nowrap xl:flex" aria-label="Основная навигация">
        <a v-for="link in navLinks" :key="link.href" :href="link.href" class="nav-link">
          {{ link.label }}
        </a>
      </nav>

      <a href="#contact" class="btn-primary hidden whitespace-nowrap px-4 py-2 text-xs xl:inline-flex">Перезвоните мне</a>

      <button
        type="button"
        class="flex h-10 w-10 items-center justify-center rounded-sm border border-white/20 text-white xl:hidden"
        :aria-expanded="menuOpen"
        :aria-label="menuOpen ? 'Закрыть меню' : 'Открыть меню'"
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
      class="border-t border-white/10 bg-navy-900 px-4 py-4 xl:hidden"
      aria-label="Мобильная навигация"
    >
      <div class="flex flex-col gap-1">
        <a
          v-for="link in navLinks"
          :key="link.href"
          :href="link.href"
          class="rounded-sm px-3 py-2.5 text-sm font-semibold uppercase tracking-wide text-slate-200 hover:bg-navy-700 hover:text-accent-500"
          @click="closeMenu"
        >
          {{ link.label }}
        </a>
        <a :href="site.phoneHref" class="btn-primary mt-3" @click="closeMenu">{{ site.phone }}</a>
      </div>
    </nav>
  </header>
</template>

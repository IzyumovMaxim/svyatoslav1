<script setup lang="ts">
import { navLinks, site } from '../data/site'

const year = new Date().getFullYear()
</script>

<template>
  <footer class="border-t border-slate-800 py-10">
    <div class="mx-auto max-w-6xl px-4 sm:px-6">
      <div class="flex flex-col items-center justify-between gap-6 sm:flex-row sm:items-center">
        <div class="flex shrink-0 items-center gap-2.5">
          <img :src="site.logo" :alt="site.title" class="h-8 w-auto" />
          <span class="whitespace-nowrap font-bold text-white">
            Волга<span class="text-accent-400">НефтеСтрой</span>
          </span>
        </div>

        <nav class="flex flex-wrap justify-center gap-x-6 gap-y-2 text-sm text-slate-400">
          <a v-for="link in navLinks" :key="link.href" :href="link.href" class="hover:text-white">
            {{ link.label }}
          </a>
        </nav>
      </div>

      <p class="mt-6 text-center text-sm leading-relaxed text-slate-500">
        &copy; {{ year }} ООО «ВолгаНефтеСтрой». {{ site.tagline }}
      </p>
    </div>
  </footer>
</template>

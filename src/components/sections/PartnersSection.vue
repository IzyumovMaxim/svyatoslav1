<script setup lang="ts">
import { reactive } from 'vue'
import { partners } from '../../data/site'

const base = import.meta.env.BASE_URL
// Пока логотипа нет в public/img/partners/, вместо него показываем название
const missingLogo = reactive<Record<string, boolean>>({})
</script>

<template>
  <section id="partners" class="section">
    <div class="container-x">
      <div class="max-w-2xl">
        <p class="section-label">С кем работаем</p>
        <h2 class="section-title">Партнёры</h2>
      </div>

      <ul class="mt-10 grid gap-6 sm:grid-cols-3">
        <li v-for="partner in partners" :key="partner.name">
          <a
            :href="partner.url"
            target="_blank"
            rel="noopener"
            class="group flex h-full flex-col items-center gap-4 border border-steel-100 bg-white p-6 text-center transition-colors hover:border-accent-500"
          >
            <div class="flex h-20 w-full items-center justify-center">
              <img
                v-if="!missingLogo[partner.name]"
                :src="base + partner.logo"
                :alt="`Логотип ${partner.name}`"
                class="max-h-20 max-w-[200px] object-contain grayscale transition group-hover:grayscale-0"
                @error="missingLogo[partner.name] = true"
              />
              <span
                v-else
                class="flex h-20 w-full items-center justify-center bg-steel-50 px-4 text-lg font-extrabold uppercase tracking-wide text-navy-800"
                aria-hidden="true"
              >
                {{ partner.name.replace(/^(ПАО|ООО)\s+/, '').replace(/[«»]/g, '') }}
              </span>
            </div>
            <span class="text-sm font-semibold text-navy-800">{{ partner.name }}</span>
          </a>
        </li>
      </ul>
    </div>
  </section>
</template>

<script setup lang="ts">
import { qualityItems } from '../../data/site'
import AppIcon from '../AppIcon.vue'
</script>

<template>
  <section id="quality" class="section">
    <div class="container-x">
      <div class="max-w-2xl">
        <p class="section-label">Лаборатории и допуски</p>
        <h2 class="section-title">Контроль качества <span class="text-accent-600">без посредников</span></h2>
      </div>

      <div class="mt-10 grid gap-6 md:grid-cols-3">
        <article
          v-for="item in qualityItems"
          :key="item.title"
          class="border-l-4 border-accent-500 bg-steel-50 p-6"
        >
          <AppIcon name="check" class="h-6 w-6 text-accent-600" />
          <h3 class="mt-4 text-base font-extrabold uppercase leading-snug text-navy-800">{{ item.title }}</h3>
          <p class="mt-3 text-sm leading-relaxed text-slate-600">{{ item.text }}</p>
        </article>
      </div>
    </div>
  </section>
</template>

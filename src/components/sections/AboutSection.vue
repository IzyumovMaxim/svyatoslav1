<script setup lang="ts">
import { aboutHighlight, aboutHighlights, aboutParagraphs } from '../../data/site'
</script>

<template>
  <section id="about" class="border-t border-slate-800/60 py-20 sm:py-28">
    <div class="mx-auto max-w-3xl px-4 sm:px-6">
      <p class="section-label">О компании</p>
      <h2 class="section-title">ООО «ВолгаНефтеСтрой»</h2>

      <div class="card mt-8 space-y-5 border-l-4 border-l-accent-500 pl-6 sm:pl-8">
        <p
          v-for="(p, i) in aboutParagraphs"
          :key="i"
          class="leading-relaxed"
          :class="i === 0 ? 'text-lg text-slate-300' : i === aboutParagraphs.length - 1 ? 'font-medium text-slate-300' : 'text-slate-400'"
        >
          {{ p }}
        </p>
        <p class="font-medium leading-relaxed text-slate-300">
          {{ aboutHighlight }}
        </p>
      </div>

      <ul class="mt-10 grid gap-4 sm:grid-cols-2">
        <li
          v-for="item in aboutHighlights"
          :key="item"
          class="flex items-center gap-3 rounded-xl border border-slate-700/50 bg-slate-800/30 px-4 py-3 text-sm text-slate-300"
        >
          <svg class="h-5 w-5 shrink-0 text-accent-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M5 13l4 4L19 7" />
          </svg>
          {{ item }}
        </li>
      </ul>
    </div>
  </section>
</template>

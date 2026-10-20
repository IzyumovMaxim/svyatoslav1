<script setup lang="ts">
import { faq } from '../../data/site'
</script>

<template>
  <section id="faq" class="section bg-steel-50">
    <div class="container-x max-w-3xl">
      <p class="section-label">Ответы</p>
      <h2 class="section-title">Частые <span class="text-accent-600">вопросы</span></h2>

      <div class="mt-10 space-y-3">
        <details v-for="item in faq" :key="item.question" class="group border border-steel-100 bg-white">
          <summary class="flex cursor-pointer list-none items-center justify-between gap-4 px-5 py-4 font-bold text-navy-800">
            {{ item.question }}
            <span class="text-xl text-accent-600 transition-transform group-open:rotate-45" aria-hidden="true">+</span>
          </summary>
          <p class="border-t border-steel-100 px-5 py-4 text-sm leading-relaxed text-slate-600">{{ item.answer }}</p>
        </details>
      </div>
    </div>
  </section>
</template>

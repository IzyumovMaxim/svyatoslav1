<script setup lang="ts">
import { stages } from '../../data/site'
</script>

<template>
  <section class="section">
    <div class="container-x">
      <div class="max-w-2xl">
        <p class="section-label">Как мы работаем</p>
        <h2 class="section-title">Этапы работы</h2>
      </div>

      <ol class="mt-10 grid gap-6 sm:grid-cols-2 lg:grid-cols-3">
        <li v-for="(stage, i) in stages" :key="stage" class="flex items-start gap-4 border-b border-steel-100 pb-6">
          <span class="text-4xl font-extrabold leading-none text-accent-500">{{ String(i + 1).padStart(2, '0') }}</span>
          <span class="pt-1 font-semibold text-navy-800">{{ stage }}</span>
        </li>
      </ol>
    </div>
  </section>
</template>

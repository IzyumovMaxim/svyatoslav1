<script setup lang="ts">
import { advantages } from '../../data/site'
import AppIcon from '../AppIcon.vue'
</script>

<template>
  <section id="advantages" class="section section-dark bg-navy-800">
    <div class="container-x">
      <div class="max-w-2xl">
        <p class="section-label">Почему мы</p>
        <h2 class="section-title">Главные преимущества</h2>
      </div>

      <div class="mt-10 grid gap-px bg-navy-700 sm:grid-cols-2 lg:grid-cols-5">
        <article v-for="(item, i) in advantages" :key="item.title" class="relative bg-navy-800 p-6">
          <span class="absolute right-5 top-4 text-3xl font-extrabold text-white/10">0{{ i + 1 }}</span>
          <div class="icon-box">
            <AppIcon :name="item.icon" class="h-6 w-6" />
          </div>
          <h3 class="mt-5 text-sm font-extrabold uppercase leading-snug text-white">{{ item.title }}</h3>
          <p class="mt-3 text-sm leading-relaxed text-slate-300">{{ item.text }}</p>
        </article>
      </div>
    </div>
  </section>
</template>

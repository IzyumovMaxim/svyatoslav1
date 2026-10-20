<script setup lang="ts">
import { equipmentPhotos, equipmentStats } from '../../data/site'
</script>

<template>
  <section id="equipment" class="section section-dark bg-navy-900">
    <div class="container-x">
      <div class="max-w-2xl">
        <p class="section-label">Парк и операторы</p>
        <h2 class="section-title">Собственная <span class="text-accent-500">техника</span></h2>
        <p class="mt-4 leading-relaxed text-slate-300">
          Не привлекаем чужую технику там, где критичны сроки: основной парк и машинисты — свои.
        </p>
      </div>

      <div class="mt-10 grid gap-px bg-navy-700 sm:grid-cols-2 lg:grid-cols-4">
        <div v-for="stat in equipmentStats" :key="stat.value" class="bg-navy-800 p-6">
          <p class="text-2xl font-extrabold text-accent-500 sm:text-3xl">{{ stat.value }}</p>
          <p class="mt-2 text-sm leading-snug text-slate-300">{{ stat.label }}</p>
        </div>
      </div>

      <div class="mt-6 grid gap-6 sm:grid-cols-2">
        <figure v-for="photo in equipmentPhotos" :key="photo.caption" class="bg-navy-800">
          <div class="photo-frame aspect-[4/3]">
            <img :src="photo.src" :alt="photo.caption" loading="lazy" />
          </div>
          <figcaption class="px-5 py-3 text-sm text-slate-300">{{ photo.caption }}</figcaption>
        </figure>
      </div>
    </div>
  </section>
</template>

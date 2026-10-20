<script setup lang="ts">
import { aboutParagraphs, aboutTerms, galleryImages } from '../../data/site'
import AppIcon from '../AppIcon.vue'
</script>

<template>
  <section id="about" class="section">
    <div class="container-x grid gap-12 lg:grid-cols-12">
      <div class="lg:col-span-7">
        <p class="section-label">О компании</p>
        <h2 class="section-title">ООО «ВолгаНефтеСтрой»</h2>

        <div class="mt-8 space-y-4 border-l-4 border-accent-500 pl-5 leading-relaxed sm:pl-6">
          <p
            v-for="(p, i) in aboutParagraphs"
            :key="i"
            :class="i === 0 ? 'text-lg font-semibold text-navy-800' : 'text-slate-600'"
          >
            {{ p }}
          </p>
        </div>

        <ul class="mt-8 grid gap-3 sm:grid-cols-2">
          <li
            v-for="term in aboutTerms"
            :key="term"
            class="flex items-center gap-3 bg-steel-50 px-4 py-3 text-sm font-semibold text-navy-800"
          >
            <AppIcon name="check" class="h-5 w-5 shrink-0 text-accent-600" />
            {{ term }}
          </li>
        </ul>
      </div>

      <div class="photo-frame aspect-[4/3] self-start border-b-4 border-accent-500 lg:col-span-5 lg:mt-16">
        <img :src="galleryImages[0].src" :alt="galleryImages[0].alt" loading="lazy" />
      </div>
    </div>
  </section>
</template>

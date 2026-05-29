<script setup lang="ts">
import { ref } from 'vue'
import { galleryImages } from '../../data/site'

const activeIndex = ref(0)

function selectImage(index: number) {
  activeIndex.value = index
}

function prev() {
  activeIndex.value = (activeIndex.value - 1 + galleryImages.length) % galleryImages.length
}

function next() {
  activeIndex.value = (activeIndex.value + 1) % galleryImages.length
}
</script>

<template>
  <section id="gallery" class="border-t border-slate-800/60 py-20 sm:py-28">
    <div class="mx-auto max-w-6xl px-4 sm:px-6">
      <div class="max-w-2xl">
        <p class="section-label">Портфолио</p>
        <h2 class="section-title">Техника и объекты</h2>
        <p class="mt-4 text-lg text-slate-400">
          Экскаваторы, подводные переходы и линейные объекты — фото с реальных проектов по всей России,
          включая северные и восточные регионы.
        </p>
      </div>

      <div class="card mt-12 overflow-hidden p-0">
        <div class="relative">
          <div class="photo-frame aspect-[16/9] w-full sm:aspect-[2/1]">
            <img
              :src="galleryImages[activeIndex].src"
              :alt="galleryImages[activeIndex].alt"
            />
          </div>
          <div class="absolute inset-x-0 bottom-0 bg-gradient-to-t from-brand-950/90 to-transparent px-6 py-4">
            <p class="text-sm text-slate-400">
              {{ activeIndex + 1 }} / {{ galleryImages.length }}
            </p>
          </div>

          <button
            type="button"
            class="absolute left-4 top-1/2 flex h-10 w-10 -translate-y-1/2 items-center justify-center rounded-full border border-slate-600 bg-brand-950/70 text-white backdrop-blur-sm transition-colors hover:border-accent-400"
            aria-label="Предыдущее фото"
            @click="prev"
          >
            <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" d="M15 19l-7-7 7-7" />
            </svg>
          </button>
          <button
            type="button"
            class="absolute right-4 top-1/2 flex h-10 w-10 -translate-y-1/2 items-center justify-center rounded-full border border-slate-600 bg-brand-950/70 text-white backdrop-blur-sm transition-colors hover:border-accent-400"
            aria-label="Следующее фото"
            @click="next"
          >
            <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
              <path stroke-linecap="round" d="M9 5l7 7-7 7" />
            </svg>
          </button>
        </div>

        <div class="grid grid-cols-4 gap-2 bg-brand-900/50 p-4 sm:grid-cols-6 lg:grid-cols-11">
          <button
            v-for="(image, index) in galleryImages"
            :key="image.alt"
            type="button"
            class="photo-frame aspect-square overflow-hidden rounded-lg border-2 transition-colors"
            :class="index === activeIndex ? 'border-accent-500' : 'border-transparent opacity-60 hover:opacity-100'"
            @click="selectImage(index)"
          >
            <img :src="image.src" :alt="image.alt" />
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

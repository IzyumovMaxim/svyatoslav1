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
  <section id="gallery" class="section bg-steel-50">
    <div class="container-x">
      <div class="max-w-2xl">
        <p class="section-label">Примеры работ</p>
        <h2 class="section-title">Техника и объекты</h2>
        <p class="mt-4 text-slate-600">
          Экскаваторы, подводные переходы и линейные объекты — фото с реальных проектов компании.
        </p>
      </div>

      <div class="mt-10 overflow-hidden bg-navy-900 shadow-sm">
        <div class="relative">
          <div class="photo-frame aspect-[4/3] w-full sm:aspect-[2/1]">
            <img
              :src="galleryImages[activeIndex].src"
              :alt="galleryImages[activeIndex].alt"
              loading="lazy"
            />
          </div>
          <div class="absolute inset-x-0 bottom-0 bg-gradient-to-t from-navy-950/90 to-transparent px-5 py-3">
            <p class="text-sm font-semibold text-slate-200">
              {{ activeIndex + 1 }} / {{ galleryImages.length }}
            </p>
          </div>

          <button
            type="button"
            class="absolute left-3 top-1/2 flex h-10 w-10 -translate-y-1/2 items-center justify-center bg-accent-500 text-navy-900 transition-colors hover:bg-accent-400"
            aria-label="Предыдущее фото"
            @click="prev"
          >
            <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
              <path stroke-linecap="round" d="M15 19l-7-7 7-7" />
            </svg>
          </button>
          <button
            type="button"
            class="absolute right-3 top-1/2 flex h-10 w-10 -translate-y-1/2 items-center justify-center bg-accent-500 text-navy-900 transition-colors hover:bg-accent-400"
            aria-label="Следующее фото"
            @click="next"
          >
            <svg class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
              <path stroke-linecap="round" d="M9 5l7 7-7 7" />
            </svg>
          </button>
        </div>

        <div class="grid grid-cols-4 gap-2 p-3 sm:grid-cols-6 lg:grid-cols-11">
          <button
            v-for="(image, index) in galleryImages"
            :key="image.alt"
            type="button"
            class="photo-frame aspect-square border-2 transition-opacity"
            :class="index === activeIndex ? 'border-accent-500' : 'border-transparent opacity-60 hover:opacity-100'"
            :aria-label="`Показать фото ${index + 1}`"
            @click="selectImage(index)"
          >
            <img :src="image.src" alt="" loading="lazy" />
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

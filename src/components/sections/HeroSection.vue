<script setup lang="ts">
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Autoplay, EffectFade } from 'swiper/modules'
import { heroSlides, site } from '../../data/site'
import 'swiper/css'
import 'swiper/css/effect-fade'

const modules = [Autoplay, EffectFade]
</script>

<template>
  <section class="relative isolate overflow-hidden bg-navy-900">
    <!-- Обёртка задаёт слой: у .swiper свой z-index:1, который перебивает утилиты Tailwind -->
    <div class="absolute inset-0 -z-10">
      <Swiper
        :modules="modules"
        :slides-per-view="1"
        :loop="true"
        :allow-touch-move="false"
        effect="fade"
        :autoplay="{ delay: 6000, disableOnInteraction: false }"
        class="hero__swiper h-full w-full"
      >
        <SwiperSlide v-for="(slide, i) in heroSlides" :key="i" class="h-full">
          <img
            :src="slide"
            :alt="i === 0 ? 'Экскаватор ООО «ВолгаНефтеСтрой» на подводном переходе' : ''"
            class="h-full w-full object-cover object-center"
            :loading="i === 0 ? 'eager' : 'lazy'"
            :fetchpriority="i === 0 ? 'high' : 'auto'"
          />
        </SwiperSlide>
      </Swiper>
      <div class="pointer-events-none absolute inset-0 z-10 bg-gradient-to-r from-navy-950/95 via-navy-900/80 to-navy-900/40" />
    </div>

    <div class="container-x flex min-h-[560px] flex-col justify-center py-16 sm:min-h-[620px] sm:py-24">
      <div class="max-w-3xl">
        <p class="section-label !text-accent-500">Действующий подрядчик ПАО «Транснефть»</p>
        <h1 class="text-3xl font-extrabold uppercase leading-tight tracking-tight text-white sm:text-4xl lg:text-5xl">
          Строительство и демонтаж
          <span class="text-accent-500">подводных переходов</span>
          магистральных трубопроводов
        </h1>
        <p class="mt-6 max-w-2xl text-base leading-relaxed text-slate-300 sm:text-lg">
          Траншейный метод, экскаваторы 220, 340, 370 со стрелами 18 м, понтоны до 90 т и лебёдки для работы
          на сильном течении. Собственная аттестованная лаборатория и НАКС.
        </p>
        <p class="mt-3 text-sm font-semibold uppercase tracking-wide text-slate-400">
          Работаем от объёмов · Цена договорная · {{ site.geography }}
        </p>
        <div class="mt-8 flex flex-col gap-3 sm:flex-row sm:gap-4">
          <a href="#contact" class="btn-primary">Перезвоните мне</a>
          <a href="#services" class="btn-outline">Виды работ</a>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero__swiper :deep(.swiper-wrapper) {
  height: 100%;
}
</style>

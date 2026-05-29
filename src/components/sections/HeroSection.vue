<script setup lang="ts">
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Autoplay, EffectFade } from 'swiper/modules'
import { companyStats, heroSlides, site } from '../../data/site'
import 'swiper/css'
import 'swiper/css/effect-fade'

const modules = [Autoplay, EffectFade]
</script>

<template>
  <section class="pt-[72px]">
    <!-- Image banner — full-width cover -->
    <div class="relative h-[200px] overflow-hidden sm:h-[260px] md:h-[320px]">
      <Swiper
        :modules="modules"
        :slides-per-view="1"
        :loop="true"
        effect="fade"
        :autoplay="{ delay: 5000, disableOnInteraction: false }"
        class="hero-banner__swiper h-full w-full"
      >
        <SwiperSlide v-for="(slide, i) in heroSlides" :key="i" class="h-full">
          <img :src="slide" :alt="`Объект ${i + 1}`" class="h-full w-full object-cover object-center" />
        </SwiperSlide>
      </Swiper>
      <div class="pointer-events-none absolute inset-0 bg-brand-950/50" />
      <div class="pointer-events-none absolute inset-0 bg-gradient-to-t from-brand-950 to-transparent" />
    </div>

    <!-- Content -->
    <div class="relative overflow-hidden bg-brand-950 pb-16 pt-12 sm:pb-20 sm:pt-14">
      <div class="pointer-events-none absolute inset-0">
        <div class="absolute -top-32 right-0 h-96 w-96 rounded-full bg-accent-500/10 blur-3xl" />
        <div class="absolute bottom-0 -left-32 h-80 w-80 rounded-full bg-teal-500/10 blur-3xl" />
      </div>

      <div class="relative mx-auto max-w-6xl px-4 sm:px-6">
        <div class="max-w-3xl">
          <p class="section-label">Подрядчик ПАО «Транснефть»</p>
          <h1 class="text-3xl font-extrabold leading-tight tracking-tight text-white sm:text-4xl lg:text-5xl">
            Полный комплекс
            <span class="text-accent-500">демонтажных работ</span>
            по всей России
          </h1>
          <p class="mt-5 max-w-2xl text-base leading-relaxed text-slate-400 sm:text-lg">
            {{ site.tagline }}. Разработка подводных траншей, демонтаж трубопроводов, работы на суше и
            болотистой местности. Базируемся в Уфе — работаем на всей территории РФ, в том числе в
            северных и восточных регионах.
          </p>
          <div class="mt-8 flex flex-wrap gap-4">
            <a :href="site.phoneHref" class="btn-primary">{{ site.phone }}</a>
            <a href="#advantages" class="btn-outline">Наши преимущества</a>
          </div>
          <p class="mt-4 text-sm text-slate-500">{{ site.phoneNote }}</p>
        </div>

        <div class="mt-12 grid grid-cols-2 gap-4 sm:grid-cols-4">
          <div v-for="stat in companyStats" :key="stat.label" class="card text-center">
            <p class="text-2xl font-extrabold text-accent-500 sm:text-3xl">{{ stat.value }}</p>
            <p class="mt-1 text-sm text-slate-400">{{ stat.label }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero-banner__swiper :deep(.swiper),
.hero-banner__swiper {
  height: 100%;
}
</style>

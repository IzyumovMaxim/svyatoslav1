<script setup lang="ts">
import { services } from '../../data/site'
import AppIcon from '../AppIcon.vue'
</script>

<template>
  <section id="services" class="section bg-steel-50">
    <div class="container-x">
      <div class="max-w-2xl">
        <p class="section-label">Что мы делаем</p>
        <h2 class="section-title">Виды работ</h2>
      </div>

      <div class="mt-10 grid gap-6 sm:grid-cols-2 lg:grid-cols-4">
        <article
          v-for="service in services"
          :key="service.title"
          class="group flex flex-col border-t-4 border-navy-800 bg-white p-6 shadow-sm transition-colors hover:border-accent-500"
        >
          <div class="icon-box">
            <AppIcon :name="service.icon" class="h-6 w-6" />
          </div>
          <h3 class="mt-5 text-base font-extrabold uppercase leading-snug text-navy-800">{{ service.title }}</h3>
          <ul class="mt-4 flex-1 space-y-2 text-sm text-slate-600">
            <li v-for="item in service.items" :key="item" class="flex gap-2">
              <span class="mt-2 h-1.5 w-1.5 shrink-0 bg-accent-500" />
              {{ item }}
            </li>
          </ul>
          <a
            href="#contact"
            class="mt-6 inline-flex items-center gap-2 text-xs font-bold uppercase tracking-wide text-navy-800 group-hover:text-accent-600"
          >
            Оставить заявку
            <span aria-hidden="true">→</span>
          </a>
        </article>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { navLinks, requisites, services, site } from '../data/site'

const year = new Date().getFullYear()
const inn = requisites.find((row) => row.label === 'ИНН / КПП')?.value
const ogrn = requisites.find((row) => row.label === 'ОГРН')?.value
</script>

<template>
  <footer class="bg-navy-950 pt-14 text-sm text-slate-400">
    <div class="container-x grid gap-10 sm:grid-cols-2 lg:grid-cols-4">
      <div class="lg:col-span-1">
        <div class="flex items-center gap-2.5">
          <img :src="site.logo" alt="Логотип ООО «ВолгаНефтеСтрой»" class="h-9 w-auto" width="36" height="36" />
          <span class="font-extrabold uppercase text-white">Волга<span class="text-accent-500">НефтеСтрой</span></span>
        </div>
        <p class="mt-4 leading-relaxed">{{ site.tagline }}. Действующий подрядчик ПАО «Транснефть».</p>
      </div>

      <div>
        <h3 class="mb-4 text-xs font-bold uppercase tracking-widest text-white">Виды работ</h3>
        <ul class="space-y-2">
          <li v-for="service in services" :key="service.title">
            <a href="#services" class="hover:text-accent-500">{{ service.title }}</a>
          </li>
        </ul>
      </div>

      <div>
        <h3 class="mb-4 text-xs font-bold uppercase tracking-widest text-white">Разделы</h3>
        <ul class="space-y-2">
          <li v-for="link in navLinks" :key="link.href">
            <a :href="link.href" class="hover:text-accent-500">{{ link.label }}</a>
          </li>
        </ul>
      </div>

      <div>
        <h3 class="mb-4 text-xs font-bold uppercase tracking-widest text-white">Контакты</h3>
        <ul class="space-y-2">
          <li><a :href="site.phoneHref" class="font-bold text-white hover:text-accent-500">{{ site.phone }}</a></li>
          <li><a :href="`mailto:${site.email}`" class="break-all hover:text-accent-500">{{ site.email }}</a></li>
          <li>{{ site.geography }}</li>
        </ul>
      </div>
    </div>

    <div class="mt-12 border-t border-white/10">
      <div class="container-x flex flex-col gap-2 py-6 text-xs sm:flex-row sm:justify-between">
        <span>&copy; {{ year }} ООО «ВолгаНефтеСтрой»</span>
        <span>ИНН/КПП {{ inn }} · ОГРН {{ ogrn }}</span>
      </div>
    </div>
  </footer>
</template>

<script setup lang="ts">
import { requisites, site } from '../../data/site'
import AppIcon from '../AppIcon.vue'
import CallbackForm from '../CallbackForm.vue'
</script>

<template>
  <section id="contact" class="section section-dark bg-navy-800">
    <div class="container-x grid gap-12 lg:grid-cols-2">
      <div>
        <p class="section-label">Контакты</p>
        <h2 class="section-title">Остались вопросы?</h2>
        <p class="mt-4 leading-relaxed text-slate-300">
          Оставьте номер — перезвоним, обсудим объект и рассчитаем стоимость. Работаем от объёмов, цена договорная.
        </p>

        <div class="mt-8 space-y-4">
          <a :href="site.phoneHref" class="flex items-center gap-4 text-white hover:text-accent-500">
            <span class="icon-box h-10 w-10"><AppIcon name="phone" class="h-5 w-5" /></span>
            <span class="text-xl font-extrabold">{{ site.phone }}</span>
          </a>
          <a :href="`mailto:${site.email}`" class="flex items-center gap-4 text-slate-200 hover:text-accent-500">
            <span class="icon-box h-10 w-10"><AppIcon name="mail" class="h-5 w-5" /></span>
            <span class="break-all">{{ site.email }}</span>
          </a>
          <p class="flex items-center gap-4 text-slate-200">
            <span class="icon-box h-10 w-10"><AppIcon name="pin" class="h-5 w-5" /></span>
            <span>Базируемся: {{ site.base }}. {{ site.geography }}.</span>
          </p>
        </div>

        <details class="group mt-8 border border-navy-700 bg-navy-900/60">
          <summary class="flex cursor-pointer list-none items-center justify-between px-5 py-4 text-sm font-bold uppercase tracking-wide text-white">
            Реквизиты организации
            <span class="text-accent-500 transition-transform group-open:rotate-45" aria-hidden="true">+</span>
          </summary>
          <dl class="space-y-3 border-t border-navy-700 px-5 py-4">
            <div v-for="row in requisites" :key="row.label">
              <dt class="text-xs font-semibold uppercase tracking-wider text-slate-400">{{ row.label }}</dt>
              <dd class="mt-0.5 text-sm text-slate-200">{{ row.value }}</dd>
            </div>
          </dl>
        </details>
      </div>

      <div class="lg:pt-10">
        <CallbackForm />
      </div>
    </div>
  </section>
</template>

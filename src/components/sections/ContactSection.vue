<script setup lang="ts">
import { contacts, geographyNote, site } from '../../data/site'
</script>

<template>
  <section id="contact" class="border-t border-slate-800/60 bg-brand-900/40 py-20 sm:py-28">
    <div class="mx-auto max-w-6xl px-4 sm:px-6">
      <div class="grid gap-12 lg:grid-cols-5">
        <div class="lg:col-span-2">
          <p class="section-label">Связаться</p>
          <h2 class="section-title">Контакты</h2>
          <p class="mt-4 leading-relaxed text-slate-400">
            {{ site.phoneNote }}
          </p>

          <div class="mt-8 space-y-4 text-sm">
            <a :href="site.phoneHref" class="flex items-center gap-3 text-slate-300 transition-colors hover:text-white">
              <svg class="h-5 w-5 shrink-0 text-accent-500" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
                <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 6.75c0 8.284 6.716 15 15 15h2.25a2.25 2.25 0 002.25-2.25v-1.372c0-.516-.351-.966-.852-1.091l-4.423-1.106c-.44-.11-.902.055-1.173.417l-.97 1.293c-.282.376-.769.542-1.21.38a12.035 12.035 0 01-7.143-7.143c-.162-.441.004-.928.38-1.21l1.293-.97c.363-.271.527-.734.417-1.173L6.963 3.102a1.125 1.125 0 00-1.091-.852H4.5A2.25 2.25 0 002.25 4.5v2.25z" />
              </svg>
              <span class="text-lg font-semibold">{{ site.phone }}</span>
            </a>
            <a :href="`mailto:${site.email}`" class="flex items-center gap-3 text-slate-300 transition-colors hover:text-white">
              <svg class="h-5 w-5 shrink-0 text-accent-500" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
                <path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75" />
              </svg>
              <span>{{ site.email }}</span>
            </a>
            <p class="flex items-start gap-3 text-slate-300">
              <svg class="mt-0.5 h-5 w-5 shrink-0 text-accent-400" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
                <path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z" />
              </svg>
              <span>{{ geographyNote }}</span>
            </p>
          </div>

          <a :href="site.phoneHref" class="btn-primary mt-10">Позвонить сейчас</a>
        </div>

        <div class="lg:col-span-3">
          <div class="card">
            <h3 class="mb-6 text-lg font-semibold text-white">Реквизиты организации</h3>
            <dl class="space-y-4">
              <div v-for="row in contacts" :key="row.label" class="border-b border-slate-700/50 pb-4 last:border-0 last:pb-0">
                <dt class="text-xs font-semibold uppercase tracking-wider text-slate-500">{{ row.label }}</dt>
                <dd class="mt-1 text-sm text-slate-300">
                  <a v-if="row.isPhone" :href="site.phoneHref" class="font-semibold text-accent-400 hover:text-accent-300">
                    {{ row.value }}
                  </a>
                  <a v-else-if="row.isEmail" :href="`mailto:${row.value}`" class="text-accent-400 hover:text-accent-300">
                    {{ row.value }}
                  </a>
                  <template v-else>{{ row.value }}</template>
                </dd>
              </div>
            </dl>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

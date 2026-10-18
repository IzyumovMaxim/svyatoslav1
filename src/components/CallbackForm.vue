<script setup lang="ts">
import { computed, ref } from 'vue'
import { formAccessKey, site } from '../data/site'

const name = ref('')
const phone = ref('')
const consent = ref(false)
const botcheck = ref(false)
const touched = ref(false)
const status = ref<'idle' | 'sending' | 'success' | 'error'>('idle')

const phoneDigits = computed(() => phone.value.replace(/\D/g, '').slice(1))
const phoneValid = computed(() => phoneDigits.value.length === 10)

// Маска +7 (XXX) XXX-XX-XX. Код страны — уже введённый «+7» или первая набранная 7/8.
// Скобку и дефисы ставим только перед следующей цифрой, чтобы стирание не упиралось в них.
function formatPhone(value: string) {
  const raw = value.replace(/\D/g, '')
  const digits = (value.startsWith('+7') || /^[78]/.test(raw) ? raw.slice(1) : raw).slice(0, 10)
  if (!digits) return raw ? '+7' : ''

  let out = `+7 (${digits.slice(0, 3)}`
  if (digits.length > 3) out += `) ${digits.slice(3, 6)}`
  if (digits.length > 6) out += `-${digits.slice(6, 8)}`
  if (digits.length > 8) out += `-${digits.slice(8, 10)}`
  return out
}

function onPhoneInput(event: Event) {
  const input = event.target as HTMLInputElement
  phone.value = formatPhone(input.value)
  input.value = phone.value
}

async function submit() {
  touched.value = true
  if (!phoneValid.value || !consent.value || status.value === 'sending') return

  if (!formAccessKey) {
    console.warn('Форма не подключена: укажите formAccessKey в src/data/site.ts')
    status.value = 'error'
    return
  }

  status.value = 'sending'
  try {
    const response = await fetch('https://api.web3forms.com/submit', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json', Accept: 'application/json' },
      body: JSON.stringify({
        access_key: formAccessKey,
        subject: 'Заявка на обратный звонок с сайта ВолгаНефтеСтрой',
        from_name: 'Сайт ВолгаНефтеСтрой',
        name: name.value.trim() || 'Не указано',
        phone: phone.value,
        botcheck: botcheck.value,
      }),
    })
    const result = await response.json()
    status.value = result.success ? 'success' : 'error'
  } catch {
    status.value = 'error'
  }
}
</script>

<template>
  <div class="bg-white p-6 shadow-xl sm:p-8">
    <div v-if="status === 'success'" class="py-10 text-center" role="status">
      <div class="mx-auto flex h-14 w-14 items-center justify-center rounded-full bg-accent-500 text-navy-900">
        <svg class="h-7 w-7" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2.5">
          <path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5" />
        </svg>
      </div>
      <p class="mt-5 text-xl font-extrabold uppercase text-navy-800">Спасибо, мы перезвоним</p>
      <p class="mt-2 text-sm text-slate-500">Обычно перезваниваем в течение рабочего дня.</p>
    </div>

    <form v-else novalidate class="space-y-4" @submit.prevent="submit">
      <h3 class="text-lg font-extrabold uppercase text-navy-800">Заказать обратный звонок</h3>
      <p class="text-sm text-slate-500">Оставьте телефон — обсудим объём работ и условия.</p>

      <div>
        <label for="cb-phone" class="mb-1.5 block text-xs font-bold uppercase tracking-wide text-navy-800">
          Телефон <span class="text-red-600">*</span>
        </label>
        <input
          id="cb-phone"
          :value="phone"
          type="tel"
          inputmode="tel"
          autocomplete="tel"
          placeholder="+7 (___) ___-__-__"
          class="field"
          :class="touched && !phoneValid && '!border-red-500'"
          :aria-invalid="touched && !phoneValid"
          aria-describedby="cb-phone-error"
          required
          @input="onPhoneInput"
        />
        <p v-if="touched && !phoneValid" id="cb-phone-error" class="mt-1 text-xs text-red-600">
          Введите номер полностью: +7 и 10 цифр
        </p>
      </div>

      <div>
        <label for="cb-name" class="mb-1.5 block text-xs font-bold uppercase tracking-wide text-navy-800">
          Имя <span class="font-medium normal-case text-slate-400">(необязательно)</span>
        </label>
        <input id="cb-name" v-model="name" type="text" autocomplete="name" placeholder="Как к вам обращаться" class="field" />
      </div>

      <input v-model="botcheck" type="checkbox" name="botcheck" class="hidden" tabindex="-1" autocomplete="off" />

      <label class="flex cursor-pointer items-start gap-3 text-xs leading-relaxed text-slate-500">
        <input v-model="consent" type="checkbox" class="mt-0.5 h-4 w-4 shrink-0 accent-accent-600" required />
        <span :class="touched && !consent && 'text-red-600'">
          Я согласен на обработку персональных данных для обратного звонка
        </span>
      </label>

      <button type="submit" class="btn-primary w-full" :disabled="status === 'sending'">
        {{ status === 'sending' ? 'Отправляем…' : 'Перезвоните мне' }}
      </button>

      <p v-if="status === 'error'" class="text-sm text-red-600" role="alert">
        Не удалось отправить заявку. Позвоните нам:
        <a :href="site.phoneHref" class="font-bold underline">{{ site.phone }}</a>
      </p>
    </form>
  </div>
</template>

<script setup lang="ts">
import { icons, type IconName } from '../data/icons'

defineProps<{ name: IconName }>()
</script>

<template>
  <svg fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5" aria-hidden="true">
    <path stroke-linecap="round" stroke-linejoin="round" :d="icons[name]" />
  </svg>
</template>

<script setup lang="ts">
import AppHeader from './components/AppHeader.vue'
import AppFooter from './components/AppFooter.vue'
import CallNowButton from './components/CallNowButton.vue'
import HeroSection from './components/sections/HeroSection.vue'
import AboutSection from './components/sections/AboutSection.vue'
import WhySection from './components/sections/WhySection.vue'
import GallerySection from './components/sections/GallerySection.vue'
import ContactSection from './components/sections/ContactSection.vue'
</script>

<template>
  <AppHeader />

  <main>
    <HeroSection />
    <AboutSection />
    <WhySection />
    <GallerySection />
    <ContactSection />
  </main>

  <AppFooter />
  <CallNowButton />
</template>

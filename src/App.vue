<script setup lang="ts">
import AppHeader from './components/AppHeader.vue'
import AppFooter from './components/AppFooter.vue'
import CallNowButton from './components/CallNowButton.vue'
import HeroSection from './components/sections/HeroSection.vue'
import AboutSection from './components/sections/AboutSection.vue'
import ServicesSection from './components/sections/ServicesSection.vue'
import WhySection from './components/sections/WhySection.vue'
import StagesSection from './components/sections/StagesSection.vue'
import GallerySection from './components/sections/GallerySection.vue'
import PartnersSection from './components/sections/PartnersSection.vue'
import ContactSection from './components/sections/ContactSection.vue'
</script>

<template>
  <AppHeader />

  <main>
    <HeroSection />
    <AboutSection />
    <ServicesSection />
    <WhySection />
    <StagesSection />
    <GallerySection />
    <PartnersSection />
    <ContactSection />
  </main>

  <AppFooter />
  <CallNowButton />
</template>

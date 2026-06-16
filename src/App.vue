<template>
  <TheNavbar />

  <HeroSection />
  <StatsSection />
  <ProgramsSection />
  <WhyUsSection />
  <TrainersSection />
  <MembershipSection />
  <GallerySection />
  <TestimonialsSection />
  <FAQSection />
  <ContactSection />

  <TheFooter />
</template>

<script setup>
import TheNavbar from './components/layout/TheNavbar.vue'
import TheFooter from './components/layout/TheFooter.vue'

import HeroSection from './components/sections/HeroSection.vue'
import StatsSection from './components/sections/StatsSection.vue'
import ProgramsSection from './components/sections/ProgramsSection.vue'
import WhyUsSection from './components/sections/WhyUsSection.vue'
import TrainersSection from './components/sections/TrainersSection.vue'
import MembershipSection from './components/sections/MembershipSection.vue'
import GallerySection from './components/sections/GallerySection.vue'
import TestimonialsSection from './components/sections/TestimonialsSection.vue'
import FAQSection from './components/sections/FAQSection.vue'
import ContactSection from './components/sections/ContactSection.vue'
</script>
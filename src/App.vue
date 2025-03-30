<template>
  <div class="app-container">
    <NavBar />
    <HeroSection />
    <DownArrow />
    <ServiceSection />
    <FeatureSection />
    <CreditSection />
    <TestimonialSection />
    <CtaSection />
    <FooterSection />
  </div>
</template>

<script>
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import DownArrow from './components/DownArrow.vue'
import ServiceSection from './components/ServiceSection.vue'
import FeatureSection from './components/FeatureSection.vue'
import CreditSection from './components/CreditSection.vue'
import TestimonialSection from './components/TestimonialSection.vue'
import CtaSection from './components/CtaSection.vue'
import FooterSection from './components/FooterSection.vue'

export default {
  components: {
    NavBar,
    HeroSection,
    DownArrow,
    ServiceSection,
    FeatureSection,
    CreditSection,
    TestimonialSection,
    CtaSection,
    FooterSection
  }
}
</script>

<style>
/* Global styles */
html, body {
  margin: 0;
  padding: 0;
  background-color: #ffffff;
}

.app-container {
  width: 100%;
  background-color: #ffffff;
  color: #000000;
}
</style>
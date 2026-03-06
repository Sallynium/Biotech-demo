<template>
  <div id="app-wrapper">
    <NavBar />
    <main>
      <HeroSection />
      <AboutSection />
      <ResearchSection />
      <ProductPipeline />
      <TeamSection />
      <NewsSection />
      <ContactSection />
    </main>
    <FooterSection />
  </div>
</template>

<script setup>
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import ResearchSection from './components/ResearchSection.vue'
import ProductPipeline from './components/ProductPipeline.vue'
import TeamSection from './components/TeamSection.vue'
import NewsSection from './components/NewsSection.vue'
import ContactSection from './components/ContactSection.vue'
import FooterSection from './components/FooterSection.vue'
</script>

<style>
#app-wrapper {
  min-height: 100vh;
}
</style>

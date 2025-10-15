<template>
  <main class="min-h-screen bg-black text-white">

    <!-- About Hero-->
    <div class="border border-white/10 w-full max-w-7xl mx-auto">
      <div class="max-w-7xl mx-auto">
        <AboutHero />
      </div>
    </div>

        <!-- Timeline Edu-->
    <div class="border border-white/10 w-full max-w-7xl mx-auto">
      <div class="max-w-7xl mx-auto">
        <EducationSection />
      </div>
    </div>

    <!-- Soft Skills coming soon -->
  </main>
</template>

<script setup>
import AboutHero from "@/components/AboutHero.vue"
import EducationSection from "@/components/EducationSection.vue"
</script>

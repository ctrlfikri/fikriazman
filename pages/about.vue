<template>
  <main class="min-h-screen bg-black text-white">
    <!-- About Hero -->
    <div class="border border-white/10 w-full max-w-7xl mx-auto">
      <AboutHero />
    </div>

    <!-- Timeline Edu -->
    <div class="border border-white/10 w-full max-w-7xl mx-auto">
      <EducationSection />
    </div>

    <!-- Who I Am Header -->
    <div class="border border-white/10 w-full max-w-7xl mx-auto">
      <WhoIAmHeader />
    </div>

    <!-- Who I Am -->
    <div class="border border-white/10 w-full max-w-7xl mx-auto">
      <WhoIAm />
    </div>

    <!-- How I Work -->
    <div class="border border-white/10 w-full max-w-7xl mx-auto">
      <HowIWork />
    </div>

    <!-- Why Work With Me -->
    <div class="border border-white/10 w-full max-w-7xl mx-auto">
      <WhyWorkWithMe />
    </div>
  </main>
</template>

<script setup>
import AboutHero from "@/components/AboutHero.vue"
import EducationSection from "@/components/EducationSection.vue"
import WhoIAm from "@/components/WhoIAm.vue"
import HowIWork from "@/components/HowIWork.vue"
import WhyWorkWithMe from "@/components/WhyWorkWithMe.vue"
import WhoIAmHeader from "../components/WhoIAmHeader.vue"
</script>
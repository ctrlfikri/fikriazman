<template>
  <section class="w-full bg-black">
  <div class="max-w-7xl mx-auto relative w-full min-h-screen bg-gradient-to-br from-blue-600 to-blue-800 overflow-x-hidden">
    <!-- Animated Coffee Bubbles Background -->
    <div class="fixed max-w-7xl mx-auto inset-0 overflow-hidden pointer-events-none z-0">
      <div
        v-for="i in 30"
        :key="`bubble-${i}`"
        class="absolute rounded-full animate-bubble-float"
        :style="{
          width: `${Math.random() * 120 + 40}px`,
          height: `${Math.random() * 120 + 40}px`,
          left: `${Math.random() * 100}%`,
          top: `${100 + Math.random() * 20}%`,
          background: `radial-gradient(circle at 30% 30%, rgba(255, 255, 255, ${Math.random() * 0.4 + 0.3}), rgba(255, 255, 255, 0.1))`,
          boxShadow: 'inset 0 0 30px rgba(255, 255, 255, 0.3)',
          animationDelay: `${Math.random() * 8}s`,
          animationDuration: `${Math.random() * 8 + 10}s`,
        }"
      />
    </div>

    <!-- Page Content -->
    <main class="relative z-10">
      <!-- Hero Section -->
      <section id="hero">
        <div class="border border-white/10 w-full max-w-7xl mx-auto">
          <DareiaHero />
        </div>
      </section>

      <!-- About Section -->
      <section id="about">
        <div class="border border-white/10 w-full max-w-7xl mx-auto">
          <DareiaAbout />
        </div>
      </section>

      <!-- Role Section -->
      <section id="role">
        <div class="border border-white/10 w-full max-w-7xl mx-auto">
          <DareiaRole />
        </div>
      </section>

            <!-- Role Section -->
      <section id="before/after">
        <div class="border border-white/10 w-full max-w-7xl mx-auto">
          <BeforeAfterSlider />
        </div>
      </section>

                  <!-- Role Section -->
      <section id="before/after">
        <div class="border border-white/10 w-full max-w-7xl mx-auto">
          <DareiaCarousel />
        </div>
      </section>

                        <!-- Role Section -->
      <section id="before/after">
        <div class="border border-white/10 w-full max-w-7xl mx-auto">
          <VisualCampaign />
        </div>
      </section>

            <section id="before/after">
        <div class="border border-white/10 w-full max-w-7xl mx-auto">
          <DareiaCTA />
        </div>
      </section>
    </main>
  </div>
</section>
</template>

<script setup>
import DareiaHero from '~/components/dareiacoffee-components/DareiaHero.vue'
import DareiaAbout from '~/components/dareiacoffee-components/DareiaAbout.vue'
import DareiaRole from '~/components/dareiacoffee-components/DareiaRole.vue'
import BeforeAfterSlider from '../../components/dareiacoffee-components/BeforeAfterSlider.vue'
import DareiaCarousel from '../../components/dareiacoffee-components/DareiaCarousel.vue'
import VisualCampaign from '../../components/dareiacoffee-components/VisualCampaign.vue'
import DareiaCTA from '../../components/dareiacoffee-components/DareiaCTA.vue'

definePageMeta({
  title: 'Dareia Coffee - Brand Identity & Design',
  description: 'Premium coffee experience with warm and inviting brand identity'
})
</script>


<style scoped>
/* Coffee Bubbles Animation */
@keyframes bubble-float {
  0% {
    transform: translateY(0) scale(0.8);
    opacity: 0;
  }
  10% {
    opacity: 0.15;
  }
  90% {
    opacity: 0.1;
  }
  100% {
    transform: translateY(-120vh) scale(1.2);
    opacity: 0;
  }
}

.animate-bubble-float {
  animation: bubble-float linear infinite;
}

/* Smooth scrolling */
html {
  scroll-behavior: smooth;
}
</style>
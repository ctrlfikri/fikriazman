<template>
  <div class="relative py-16 sm:py-20 md:py-24 lg:py-32 px-4 sm:px-6 lg:px-8 bg-white/5 backdrop-blur-sm">
    <div class="max-w-7xl mx-auto">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 lg:gap-12 xl:gap-16 items-center">
        
        <!-- Image (Left on Desktop) -->
        <div class="relative order-2 lg:order-1">
          <div class="relative rounded-3xl overflow-hidden shadow-2xl transform hover:scale-105 transition-transform duration-500">
            <!-- Placeholder for banner image -->
            <div class="aspect-[16/9] bg-white/10 backdrop-blur-sm flex items-center justify-center">
              <div class="text-center text-white/60">
                <img 
                  src="/banner.jpg"
                  alt="Cafe Exterior"
                  class="w-full h-full object-cover"
                />
              </div>
            </div>
            
            <!-- Decorative Border -->
            <div class="absolute inset-0 border-4 border-white/20 rounded-3xl pointer-events-none" />
          </div>

          <!-- Floating Elements -->
          <div class="absolute -bottom-6 -left-6 w-24 h-24 sm:w-32 sm:h-32 bg-yellow-400 rounded-full blur-3xl opacity-30 animate-pulse" />
          <div class="absolute -top-6 -right-6 w-32 h-32 sm:w-40 sm:h-40 bg-blue-300 rounded-full blur-3xl opacity-20 animate-pulse" style="animation-delay: 1s" />
        </div>

        <!-- Text Content (Right on Desktop) -->
        <div class="space-y-6 sm:space-y-8 order-1 lg:order-2">
          <!-- Section Label -->
          <div class="inline-block px-4 py-2 bg-white/20 backdrop-blur-sm rounded-full">
            <p class="text-white/90 font-semibold text-sm sm:text-base">My Contribution</p>
          </div>

          <!-- Heading -->
          <h2 class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-black text-white leading-tight">
            Brewing a<br />Visual Identity
          </h2>

          <!-- Description -->
          <div class="space-y-4 text-white/80 text-base sm:text-lg md:text-xl leading-relaxed">
            <p>
              As the <span class="text-white font-bold">Graphic Designer & Brand Identity Specialist</span>, I transformed Dareia Coffee's visual presence from the ground up. My role encompassed every touchpoint of the customer experience.
            </p>
          </div>

          <!-- Services Grid -->
          <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 pt-4">
            <div 
              v-for="service in services" 
              :key="service.id"
              class="bg-white/10 backdrop-blur-md rounded-2xl p-4 sm:p-6 border border-white/20 hover:bg-white/20 transition-all duration-300 transform hover:scale-105"
            >
              <div class="flex items-start gap-3 sm:gap-4">
                <div class="flex-shrink-0 w-10 h-10 sm:w-12 sm:h-12 bg-white/20 rounded-xl flex items-center justify-center">
                  <span class="text-xl sm:text-2xl">{{ service.icon }}</span>
                </div>
                <div>
                  <h3 class="text-white font-bold text-base sm:text-lg mb-1">{{ service.title }}</h3>
                  <p class="text-white/70 text-sm sm:text-base">{{ service.desc }}</p>
                </div>
              </div>
            </div>
          </div>

          <!-- Key Achievement -->
          <div class="bg-gradient-to-r from-white/20 to-white/10 backdrop-blur-md rounded-2xl p-6 sm:p-8 border border-white/30">
            <p class="text-white/90 text-base sm:text-lg md:text-xl leading-relaxed">
              <span class="font-black text-white text-xl sm:text-2xl">"</span>
              Elevated the brand from a local café to a recognized coffee destination through cohesive visual storytelling and strategic design.
              <span class="font-black text-white text-xl sm:text-2xl">"</span>
            </p>
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script setup>
const services = [
  {
    id: 1,
    icon: '🎨',
    title: 'Brand Identity',
    desc: 'Logo design, color palette, and visual guidelines'
  },
  {
    id: 2,
    icon: '📱',
    title: 'Social Media',
    desc: 'Instagram posts, stories, and promotional content'
  },
  {
    id: 3,
    icon: '📋',
    title: 'Menu Design',
    desc: 'Complete menu overhaul with modern aesthetics'
  },
  {
    id: 4,
    icon: '🎯',
    title: 'Marketing Materials',
    desc: 'Banners, posters, and campaign visuals'
  }
]
</script>

<style scoped>
/* Subtle pulse animation */
@keyframes pulse {
  0%, 100% {
    opacity: 0.2;
  }
  50% {
    opacity: 0.4;
  }
}
</style>
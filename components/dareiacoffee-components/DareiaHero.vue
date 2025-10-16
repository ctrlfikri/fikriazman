<template>
  <div class="relative min-h-screen flex items-center justify-center px-4 sm:px-6 lg:px-8 pt-20 sm:pt-24">
    <div class="max-w-7xl mx-auto w-full">
      <div class="text-center space-y-6 sm:space-y-8">
        <!-- Main Logo -->
        <div class="animate-fade-in-up">
          <img 
            src="/dclogo.png" 
            alt="Dareia Coffee Logo" 
            class="h-24 sm:h-32 md:h-40 lg:h-48 xl:h-56 w-auto mx-auto drop-shadow-2xl"
          />
        </div>

        <!-- Title -->
        <h1 
          class="text-5xl sm:text-6xl md:text-7xl lg:text-8xl xl:text-9xl font-black text-white leading-tight animate-fade-in-up tracking-tight"
          style="animation-delay: 0.1s"
        >
          Dareia Coffee
        </h1>

        <!-- Subtitle -->
        <p 
          class="text-xl sm:text-2xl md:text-3xl lg:text-4xl text-white/90 font-semibold animate-fade-in-up max-w-3xl mx-auto"
          style="animation-delay: 0.2s"
        >
          Graphic Designer & Brand Identity
        </p>

        <!-- Description -->
        <p 
          class="text-base sm:text-lg md:text-xl lg:text-2xl text-white/80 max-w-2xl mx-auto leading-relaxed animate-fade-in-up"
          style="animation-delay: 0.3s"
        >
          Crafted a warm and inviting brand identity for a premium coffee experience that brings people together.
        </p>

        <!-- CTA Buttons -->
        <div 
          class="flex flex-col sm:flex-row gap-4 sm:gap-6 justify-center items-center pt-6 sm:pt-8 animate-fade-in-up"
          style="animation-delay: 0.4s"
        >
          <a
            href="#about"
            class="group relative px-8 sm:px-10 md:px-12 py-4 sm:py-5 bg-white text-blue-700 font-bold text-base sm:text-lg md:text-xl rounded-2xl shadow-2xl hover:shadow-white/30 transform hover:scale-105 transition-all duration-300 overflow-hidden w-full sm:w-auto"
          >
            <span class="relative z-10 flex items-center justify-center gap-2">
              Explore My Work
              <svg class="w-5 h-5 sm:w-6 sm:h-6 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
              </svg>
            </span>
            <div class="absolute inset-0 bg-gradient-to-r from-transparent via-blue-100 to-transparent translate-x-[-200%] group-hover:translate-x-[200%] transition-transform duration-1000" />
          </a>

          <a
            href="https://instagram.com/dareiacoffee"
            target="_blank"
            rel="noopener noreferrer"
            class="px-8 sm:px-10 md:px-12 py-4 sm:py-5 border-3 border-white text-white font-bold text-base sm:text-lg md:text-xl rounded-2xl hover:bg-white/10 backdrop-blur-sm transform hover:scale-105 transition-all duration-300 w-full sm:w-auto text-center"
          >
            Visit Instagram ↗
          </a>
        </div>

        <!-- Scroll Indicator -->
        <div class="pt-12 sm:pt-16 md:pt-20 animate-bounce">
          <svg class="w-6 h-6 sm:w-8 sm:h-8 mx-auto text-white/60" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3" />
          </svg>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
// No state needed for this component
</script>

<style scoped>
/* Fade In Up Animation */
@keyframes fade-in-up {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in-up {
  animation: fade-in-up 0.8s ease-out forwards;
  opacity: 0;
}
</style>
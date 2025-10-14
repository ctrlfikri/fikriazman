<template>
  <!-- Left: Section Title - Enhanced Minimal Design -->
  <div class="lg:w-1/3 text-center border border-white/10 p-6 sm:p-8 md:p-10 lg:p-12 flex flex-col justify-center bg-black relative overflow-hidden">
    <!-- Subtle grid pattern -->
    <div class="absolute inset-0 opacity-[0.02]" style="background-image: radial-gradient(circle, white 1px, transparent 1px); background-size: 20px 20px;"></div>
    
    <!-- Minimal corner accents -->
    <div class="absolute top-0 left-0 w-12 h-12 border-t-2 border-l-2 border-white/20"></div>
    <div class="absolute top-0 right-0 w-12 h-12 border-t-2 border-r-2 border-white/20"></div>
    <div class="absolute bottom-0 left-0 w-12 h-12 border-b-2 border-l-2 border-white/20"></div>
    <div class="absolute bottom-0 right-0 w-12 h-12 border-b-2 border-r-2 border-white/20"></div>

    <div class="relative z-10">
      <!-- Avatar with subtle pulsing ring -->
      <div class="relative w-20 h-20 sm:w-24 sm:h-24 md:w-28 md:h-28 mx-auto mb-6 sm:mb-8">
        <!-- Outer ring -->
        <div class="absolute inset-0 rounded-full border border-white/10 animate-ping-slow"></div>
        
        <!-- Avatar -->
        <div class="relative w-full h-full rounded-full overflow-hidden ring-2 ring-white/20 ring-offset-4 ring-offset-black">
          <img
            src="/avatar.jpeg"
            alt="Avatar"
            class="w-full h-full object-cover"
          />
          <div class="absolute inset-0 rounded-full border border-white/10 glow-animation"></div>
        </div>
      </div>

      <!-- Title with typing cursor effect -->
      <div class="mb-3 sm:mb-4 flex items-baseline justify-center">
        <h1 class="text-3xl sm:text-3xl md:text-4xl lg:text-5xl font-bold text-white tracking-wider">
          MY SKILLS<span class="animate-blink-cursor">_</span>
        </h1>
      </div>

      <!-- Subtle divider line -->
      <div class="w-16 h-[1px] bg-gradient-to-r from-transparent via-white/30 to-transparent mx-auto mb-4 sm:mb-6"></div>

      <!-- Description -->
      <p class="text-gray-400 text-base sm:text-lg md:text-xl px-4 leading-relaxed font-light">
        A glance at what I can do<br/>and how proficient I am
      </p>

      <!-- Minimal stats -->
      <div class="mt-6 sm:mt-8 flex justify-center gap-8 sm:gap-12">
        <div class="text-center">
          <div class="text-2xl sm:text-3xl font-bold text-white font-mono">10+</div>
          <div class="text-[10px] sm:text-xs text-gray-500 uppercase tracking-widest mt-1">Skills</div>
        </div>
        <div class="w-[1px] bg-white/10"></div>
        <div class="text-center">
          <div class="text-2xl sm:text-3xl font-bold text-white font-mono">4</div>
          <div class="text-[10px] sm:text-xs text-gray-500 uppercase tracking-widest mt-1">Categories</div>
        </div>
      </div>

      <!-- Scroll indicator (only visible on mobile) -->
      <div class="lg:hidden mt-8 flex flex-col items-center gap-2 opacity-50">
        <span class="text-xs text-gray-500 uppercase tracking-wider">Swipe to explore</span>
        <div class="flex gap-1">
          <div class="w-1 h-1 rounded-full bg-white/30 animate-pulse"></div>
          <div class="w-1 h-1 rounded-full bg-white/30 animate-pulse" style="animation-delay: 0.2s;"></div>
          <div class="w-1 h-1 rounded-full bg-white/30 animate-pulse" style="animation-delay: 0.4s;"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
</script>

<style scoped>
@keyframes pulse-glow {
  0% {
    box-shadow: 0 0 5px 2px rgba(255, 255, 255, 0.3),
      0 0 10px 5px rgba(255, 255, 255, 0.2);
  }
  50% {
    box-shadow: 0 0 15px 5px rgba(255, 255, 255, 0.6),
      0 0 25px 10px rgba(255, 255, 255, 0.4);
  }
  100% {
    box-shadow: 0 0 5px 2px rgba(255, 255, 255, 0.3),
      0 0 10px 5px rgba(255, 255, 255, 0.2);
  }
}

.glow-animation {
  animation: pulse-glow 2s ease-in-out infinite;
}

/* Typing cursor blink */
@keyframes blink-cursor {
  0%, 49% { opacity: 1; }
  50%, 100% { opacity: 0; }
}

.animate-blink-cursor {
  animation: blink-cursor 1s step-start infinite;
}

/* Slow ping animation */
@keyframes ping-slow {
  0% {
    transform: scale(1);
    opacity: 0.5;
  }
  50% {
    transform: scale(1.1);
    opacity: 0.2;
  }
  100% {
    transform: scale(1.2);
    opacity: 0;
  }
}

.animate-ping-slow {
  animation: ping-slow 3s cubic-bezier(0, 0, 0.2, 1) infinite;
}
</style>
<template>
  <!-- Projects Section - LED Board Style -->
  <div class="w-full h-600 border border-white/10 py-12 sm:py-8 md:py-12 lg:py-18 flex justify-center items-center overflow-hidden relative">
    <!-- LED Dotted Background - Enhanced -->
    <svg class="absolute inset-0 w-full opacity-80" viewBox="0 0 1200 300" preserveAspectRatio="none">
      <defs>
        <!-- LED dot pattern -->
        <pattern id="led-dots" x="0" y="0" width="15" height="15" patternUnits="userSpaceOnUse">
          <rect x="0" y="0" width="15" height="15" fill="#0a0a0a"/>
          <circle cx="7.5" cy="7.5" r="1.5" fill="#1a1a1a" opacity="0.8">
            <animate attributeName="opacity" values="0.3;0.6;0.3" dur="4s" repeatCount="indefinite"/>
          </circle>
        </pattern>
        
        <!-- Scanline effect -->
        <linearGradient id="scanline" x1="0%" y1="0%" x2="0%" y2="100%">
          <stop offset="0%" style="stop-color:#000;stop-opacity:0" />
          <stop offset="50%" style="stop-color:#ffeb3b;stop-opacity:0.1" />
          <stop offset="100%" style="stop-color:#000;stop-opacity:0" />
        </linearGradient>
      </defs>
      
      <rect width="1200" height="300" fill="#000"/>
      <rect width="1200" height="300" fill="url(#led-dots)"/>
      
      <!-- Animated scanline -->
      <rect width="1200" height="80" fill="url(#scanline)" opacity="0.5">
        <animate attributeName="y" from="-80" to="300" dur="3s" repeatCount="indefinite"/>
      </rect>
    </svg>

    <!-- Text Overlay - Responsive -->
    <div class="relative flex flex-col items-center justify-center px-4 sm:px-6 md:px-8 z-10">
      <!-- Main LED Text -->
      <div class="relative mb-4 sm:mb-6">
        <h1
          class="font-monospace text-white text-3xl sm:text-4xl md:text-5xl lg:text-6xl xl:text-7xl font-black text-center leading-tight tracking-wider"
          style="text-shadow: 0 0 20px rgba(255, 255, 255, 0.2), 0 0 40px rgba(255, 255, 255, 0.5), 0 0 60px rgba(255, 255, 255, 0.3);"
        >
          MY PROJECTS
        </h1>
      </div>

      <!-- Divider line with animation -->
      <div class="w-full max-w-md h-[2px] bg-gradient-to-r from-transparent via-yellow-500/50 to-transparent mb-4 relative overflow-hidden">
        <div class="absolute inset-0 bg-gradient-to-r from-transparent via-yellow-400 to-transparent animate-scan-horizontal"></div>
      </div>

      <!-- Subtitle -->
      <p class="text-gray-400 font-monospace text-sm sm:text-base md:text-lg lg:text-xl text-center max-w-2xl leading-relaxed px-2">
        <span class="text-yellow-500/70">&gt;</span> SEE WHAT I HAVE BEEN INVOLVED IN
      </p>

      <!-- LED Status Bar -->
      <div class="mt-6 sm:mt-8 flex items-center gap-2 sm:gap-3">
        <div class="flex gap-1">
          <div class="w-1.5 h-1.5 sm:w-2 sm:h-2 rounded-full bg-yellow-500 animate-blink" style="animation-delay: 0s;"></div>
          <div class="w-1.5 h-1.5 sm:w-2 sm:h-2 rounded-full bg-yellow-500 animate-blink" style="animation-delay: 0.2s;"></div>
          <div class="w-1.5 h-1.5 sm:w-2 sm:h-2 rounded-full bg-yellow-500 animate-blink" style="animation-delay: 0.4s;"></div>
        </div>
        <span class="text-[10px] sm:text-xs text-yellow-500/50 font-monospace uppercase tracking-widest">3 Total Project (Exclude Freelancing)</span>
      </div>
    </div>

    <!-- Grid overlay for extra depth -->
    <div class="absolute inset-0 opacity-5 pointer-events-none" 
         style="background-image: linear-gradient(rgba(255,255,255,.03) 1px, transparent 1px), linear-gradient(90deg, rgba(255,255,255,.03) 1px, transparent 1px); background-size: 50px 50px;">
    </div>
  </div>
</template>

<script setup>
</script>

<style scoped>
/* Blinking LED effect */
@keyframes blink {
  0%, 49% { opacity: 1; }
  50%, 100% { opacity: 0.2; }
}

.animate-blink {
  animation: blink 1s step-start infinite;
}

/* Horizontal scan animation */
@keyframes scan-horizontal {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(100%); }
}

.animate-scan-horizontal {
  animation: scan-horizontal 2s ease-in-out infinite;
}
</style>
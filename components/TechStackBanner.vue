<template>
  <div class="w-full border border-white/10 py-16 sm:py-20 lg:py-24 flex justify-center items-center overflow-hidden relative">
    <svg class="absolute inset-0 w-full opacity-80" viewBox="0 0 1200 300" preserveAspectRatio="none">
      <defs>
        <pattern id="led-dots-stack" x="0" y="0" width="15" height="15" patternUnits="userSpaceOnUse">
          <rect x="0" y="0" width="15" height="15" fill="#0a0a0a"/>
          <circle cx="7.5" cy="7.5" r="1.5" fill="#1a1a1a" opacity="0.8">
            <animate attributeName="opacity" values="0.3;0.6;0.3" dur="4s" repeatCount="indefinite"/>
          </circle>
        </pattern>
        
        <linearGradient id="scanline-stack" x1="0%" y1="0%" x2="0%" y2="100%">
          <stop offset="0%" style="stop-color:#000;stop-opacity:0" />
          <stop offset="50%" style="stop-color:#00d4ff;stop-opacity:0.1" />
          <stop offset="100%" style="stop-color:#000;stop-opacity:0" />
        </linearGradient>
      </defs>
      
      <rect width="1200" height="300" fill="#000"/>
      <rect width="1200" height="300" fill="url(#led-dots-stack)"/>
      
      <rect width="1200" height="80" fill="url(#scanline-stack)" opacity="0.5">
        <animate attributeName="y" from="-80" to="300" dur="3s" repeatCount="indefinite"/>
      </rect>
    </svg>

    <div class="relative flex flex-col items-center justify-center px-4 sm:px-6 md:px-8 z-10 w-full max-w-6xl">
      <!-- Title -->
      <div class="relative mb-4 sm:mb-6">
        <h1
          class="font-monospace text-white text-3xl sm:text-4xl md:text-5xl lg:text-6xl font-black text-center leading-tight tracking-wider"
          style="text-shadow: 0 0 20px rgba(0, 212, 255, 0.3), 0 0 40px rgba(0, 212, 255, 0.5), 0 0 60px rgba(0, 212, 255, 0.3);"
        >
          CURRENT STACK
        </h1>
      </div>

      <!-- Divider line with animation -->
      <div class="w-full max-w-md h-[2px] bg-gradient-to-r from-transparent via-cyan-500/50 to-transparent mb-3 relative overflow-hidden">
        <div class="absolute inset-0 bg-gradient-to-r from-transparent via-cyan-400 to-transparent animate-scan-horizontal"></div>
      </div>

      <!-- Subtitle -->
      <p class="text-gray-400 font-monospace text-xs sm:text-sm md:text-base text-center max-w-2xl leading-relaxed px-2 mb-10 sm:mb-12">
        <span class="text-cyan-500/70">&gt;</span> I'M INTERESTED IN DEVELOPING WITH THESE TECHNOLOGIES
      </p>

      <!-- Flowchart - Desktop Layout -->
      <div class="hidden lg:flex items-center justify-center gap-6 w-full">
        <!-- Frontend -->
        <div class="flex flex-col items-center">
          <div class="px-6 py-4 bg-cyan-500/10 border-2 border-cyan-500/40 rounded-lg font-monospace text-lg text-cyan-400 uppercase tracking-wider animate-pulse-glow relative flex flex-col items-center gap-3">
            <div class="absolute -top-8 left-1/2 -translate-x-1/2 text-[10px] text-cyan-500/50 uppercase tracking-widest whitespace-nowrap">Frontend</div>
            <img src="/nuxt.png" alt="Nuxt.js" class="w-8 h-8 object-contain icon-glow-cyan" />
            <span>Nuxt.js</span>
          </div>
        </div>

        <!-- Arrow 1 -->
        <div class="flex items-center gap-2">
          <div class="w-12 h-[2px] bg-gradient-to-r from-cyan-500/50 to-cyan-500/20 relative overflow-hidden">
            <div class="absolute inset-0 bg-gradient-to-r from-transparent via-cyan-400 to-transparent animate-flow"></div>
          </div>
          <div class="w-0 h-0 border-t-[6px] border-t-transparent border-l-[12px] border-l-cyan-500/50 border-b-[6px] border-b-transparent"></div>
        </div>

        <!-- Backend -->
        <div class="flex flex-col items-center">
          <div class="px-6 py-4 bg-cyan-500/10 border-2 border-cyan-500/40 rounded-lg font-monospace text-lg text-cyan-400 uppercase tracking-wider animate-pulse-glow relative flex flex-col items-center gap-3" style="animation-delay: 0.2s;">
            <div class="absolute -top-8 left-1/2 -translate-x-1/2 text-[10px] text-cyan-500/50 uppercase tracking-widest whitespace-nowrap">Backend</div>
            <img src="/django.png" alt="Django" class="w-8 h-8 object-contain icon-glow-cyan" />
            <span>Django</span>
          </div>
        </div>

        <!-- Arrow 2 -->
        <div class="flex items-center gap-2">
          <div class="w-12 h-[2px] bg-gradient-to-r from-cyan-500/50 to-cyan-500/20 relative overflow-hidden">
            <div class="absolute inset-0 bg-gradient-to-r from-transparent via-cyan-400 to-transparent animate-flow" style="animation-delay: 0.3s;"></div>
          </div>
          <div class="w-0 h-0 border-t-[6px] border-t-transparent border-l-[12px] border-l-cyan-500/50 border-b-[6px] border-b-transparent"></div>
        </div>

        <!-- Database -->
        <div class="flex flex-col items-center">
          <div class="px-6 py-4 bg-cyan-500/10 border-2 border-cyan-500/40 rounded-lg font-monospace text-lg text-cyan-400 uppercase tracking-wider animate-pulse-glow relative flex flex-col items-center gap-3" style="animation-delay: 0.4s;">
            <div class="absolute -top-8 left-1/2 -translate-x-1/2 text-[10px] text-cyan-500/50 uppercase tracking-widest whitespace-nowrap">Database</div>
            <img src="/postgre.png" alt="PostgreSQL" class="w-8 h-8 object-contain icon-glow-cyan" />
            <span>PostgreSQL</span>
          </div>
        </div>

        <!-- Curved connection to Automation -->
        <svg class="w-24 h-24 -ml-2 -mr-2" viewBox="0 0 100 100">
          <defs>
            <linearGradient id="curve-gradient" x1="0%" y1="0%" x2="100%" y2="0%">
              <stop offset="0%" style="stop-color:rgba(0,212,255,0.5);stop-opacity:1" />
              <stop offset="100%" style="stop-color:rgba(234,179,8,0.5);stop-opacity:1" />
            </linearGradient>
          </defs>
          <path d="M 10 50 Q 50 20, 90 50" stroke="url(#curve-gradient)" stroke-width="2" fill="none">
            <animate attributeName="stroke-dasharray" from="0,200" to="200,0" dur="2s" repeatCount="indefinite"/>
          </path>
          <polygon points="90,50 82,46 82,54" fill="rgba(234,179,8,0.5)"/>
        </svg>

        <!-- Automation -->
        <div class="flex flex-col items-center">
          <div class="px-6 py-4 bg-yellow-500/10 border-2 border-yellow-500/40 rounded-lg font-monospace text-lg text-yellow-400 uppercase tracking-wider animate-pulse-glow-yellow relative flex flex-col items-center gap-3" style="animation-delay: 0.6s;">
            <div class="absolute -top-8 left-1/2 -translate-x-1/2 text-[10px] text-yellow-500/50 uppercase tracking-widest whitespace-nowrap">Automation</div>
            <img src="/n8n.png" alt="n8n" class="w-8 h-8 object-contain icon-glow-yellow" />
            <span>n8n</span>
          </div>
        </div>
      </div>

      <!-- Flowchart - Mobile/Tablet Layout (Horizontal Scroll) -->
      <div class="lg:hidden w-full overflow-x-auto pb-4 scrollbar-hide">
        <div class="flex items-center gap-4 min-w-max px-4">
          <!-- Frontend -->
          <div class="flex flex-col items-center">
            <div class="text-[10px] text-cyan-500/50 uppercase tracking-widest mb-3 whitespace-nowrap">Frontend</div>
            <div class="px-6 py-3 bg-cyan-500/10 border-2 border-cyan-500/40 rounded-lg font-monospace text-sm text-cyan-400 uppercase tracking-wider animate-pulse-glow whitespace-nowrap flex flex-col items-center gap-2">
              <img src="/nuxt.png" alt="Nuxt.js" class="w-6 h-6 object-contain icon-glow-cyan" />
              <span>Nuxt.js</span>
            </div>
          </div>

          <!-- Arrow Right -->
          <div class="flex items-center gap-1">
            <div class="w-8 h-[2px] bg-gradient-to-r from-cyan-500/50 to-cyan-500/20 relative overflow-hidden">
              <div class="absolute inset-0 bg-gradient-to-r from-transparent via-cyan-400 to-transparent animate-flow"></div>
            </div>
            <div class="w-0 h-0 border-t-[6px] border-t-transparent border-l-[12px] border-l-cyan-500/50 border-b-[6px] border-b-transparent"></div>
          </div>

          <!-- Backend -->
          <div class="flex flex-col items-center">
            <div class="text-[10px] text-cyan-500/50 uppercase tracking-widest mb-3 whitespace-nowrap">Backend</div>
            <div class="px-6 py-3 bg-cyan-500/10 border-2 border-cyan-500/40 rounded-lg font-monospace text-sm text-cyan-400 uppercase tracking-wider animate-pulse-glow whitespace-nowrap flex flex-col items-center gap-2" style="animation-delay: 0.2s;">
              <img src="/django.png" alt="Django" class="w-6 h-6 object-contain icon-glow-cyan" />
              <span>Django</span>
            </div>
          </div>

          <!-- Arrow Right -->
          <div class="flex items-center gap-1">
            <div class="w-8 h-[2px] bg-gradient-to-r from-cyan-500/50 to-cyan-500/20 relative overflow-hidden">
              <div class="absolute inset-0 bg-gradient-to-r from-transparent via-cyan-400 to-transparent animate-flow" style="animation-delay: 0.3s;"></div>
            </div>
            <div class="w-0 h-0 border-t-[6px] border-t-transparent border-l-[12px] border-l-cyan-500/50 border-b-[6px] border-b-transparent"></div>
          </div>

          <!-- Database -->
          <div class="flex flex-col items-center">
            <div class="text-[10px] text-cyan-500/50 uppercase tracking-widest mb-3 whitespace-nowrap">Database</div>
            <div class="px-6 py-3 bg-cyan-500/10 border-2 border-cyan-500/40 rounded-lg font-monospace text-sm text-cyan-400 uppercase tracking-wider animate-pulse-glow whitespace-nowrap flex flex-col items-center gap-2" style="animation-delay: 0.4s;">
              <img src="/postgre.png" alt="PostgreSQL" class="w-6 h-6 object-contain icon-glow-cyan" />
              <span>PostgreSQL</span>
            </div>
          </div>

          <!-- Arrow Right -->
          <div class="flex items-center gap-1">
            <div class="w-8 h-[2px] bg-gradient-to-r from-cyan-500/50 to-yellow-500/50 relative overflow-hidden">
              <div class="absolute inset-0 bg-gradient-to-r from-transparent via-yellow-400 to-transparent animate-flow" style="animation-delay: 0.5s;"></div>
            </div>
            <div class="w-0 h-0 border-t-[6px] border-t-transparent border-l-[12px] border-l-yellow-500/50 border-b-[6px] border-b-transparent"></div>
          </div>

          <!-- Automation -->
          <div class="flex flex-col items-center">
            <div class="text-[10px] text-yellow-500/50 uppercase tracking-widest mb-3 whitespace-nowrap">Automation</div>
            <div class="px-6 py-3 bg-yellow-500/10 border-2 border-yellow-500/40 rounded-lg font-monospace text-sm text-yellow-400 uppercase tracking-wider animate-pulse-glow-yellow whitespace-nowrap flex flex-col items-center gap-2" style="animation-delay: 0.6s;">
              <img src="/n8n.png" alt="n8n" class="w-6 h-6 object-contain icon-glow-yellow" />
              <span>n8n</span>
            </div>
          </div>
        </div>
        
        <!-- Scroll hint -->
        <div class="flex justify-center mt-4 gap-1 opacity-50">
          <div class="w-1 h-1 rounded-full bg-cyan-500/50 animate-pulse"></div>
          <div class="w-1 h-1 rounded-full bg-cyan-500/50 animate-pulse" style="animation-delay: 0.2s;"></div>
          <div class="w-1 h-1 rounded-full bg-cyan-500/50 animate-pulse" style="animation-delay: 0.4s;"></div>
        </div>
      </div>

      <!-- LED Status Bar -->
      <div class="mt-8 sm:mt-12 flex items-center gap-2 sm:gap-3">
        <div class="flex gap-1">
          <div class="w-1.5 h-1.5 sm:w-2 sm:h-2 rounded-full bg-cyan-500 animate-blink" style="animation-delay: 0s;"></div>
          <div class="w-1.5 h-1.5 sm:w-2 sm:h-2 rounded-full bg-cyan-500 animate-blink" style="animation-delay: 0.2s;"></div>
          <div class="w-1.5 h-1.5 sm:w-2 sm:h-2 rounded-full bg-cyan-500 animate-blink" style="animation-delay: 0.4s;"></div>
        </div>
        <span class="text-[10px] sm:text-xs text-cyan-500/50 font-monospace uppercase tracking-widest">Full Stack Pipeline Active</span>
      </div>
    </div>

    <div class="absolute inset-0 opacity-5 pointer-events-none" 
         style="background-image: linear-gradient(rgba(0,212,255,.03) 1px, transparent 1px), linear-gradient(90deg, rgba(0,212,255,.03) 1px, transparent 1px); background-size: 50px 50px;">
    </div>
  </div>
</template>

<script setup>
</script>

<style scoped>
/* Hide scrollbar but keep functionality */
.scrollbar-hide {
  -ms-overflow-style: none;
  scrollbar-width: none;
}

.scrollbar-hide::-webkit-scrollbar {
  display: none;
}

@keyframes blink {
  0%, 49% { opacity: 1; }
  50%, 100% { opacity: 0.2; }
}

.animate-blink {
  animation: blink 1s step-start infinite;
}

@keyframes scan-horizontal {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(100%); }
}

.animate-scan-horizontal {
  animation: scan-horizontal 2s ease-in-out infinite;
}

@keyframes flow {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(100%); }
}

.animate-flow {
  animation: flow 1.5s ease-in-out infinite;
}

@keyframes pulse-glow {
  0%, 100% { 
    opacity: 0.7;
    box-shadow: 0 0 10px rgba(0, 212, 255, 0.3), 0 0 20px rgba(0, 212, 255, 0.2);
  }
  50% { 
    opacity: 1;
    box-shadow: 0 0 20px rgba(0, 212, 255, 0.6), 0 0 40px rgba(0, 212, 255, 0.4);
  }
}

.animate-pulse-glow {
  animation: pulse-glow 2s ease-in-out infinite;
}

@keyframes pulse-glow-yellow {
  0%, 100% { 
    opacity: 0.7;
    box-shadow: 0 0 10px rgba(234, 179, 8, 0.3), 0 0 20px rgba(234, 179, 8, 0.2);
  }
  50% { 
    opacity: 1;
    box-shadow: 0 0 20px rgba(234, 179, 8, 0.6), 0 0 40px rgba(234, 179, 8, 0.4);
  }
}

.animate-pulse-glow-yellow {
  animation: pulse-glow-yellow 2s ease-in-out infinite;
}

/* Icon glow effects */
.icon-glow-cyan {
  filter: drop-shadow(0 0 8px rgba(0, 212, 255, 0.5));
}

.icon-glow-yellow {
  filter: drop-shadow(0 0 8px rgba(234, 179, 8, 0.5));
}
</style>
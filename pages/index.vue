<template>
  <div class="flex flex-col bg-black">
    <!-- Hero -->
    <div class="w-full bg-black">
      <div class="border border-white/10 w-full max-w-7xl mx-auto">
        <HeroSection />
      </div>
    </div>

    <!-- Skills -->
    <div class="w-full bg-black">
      <div class="max-w-7xl mx-auto">
        <div class="flex flex-col lg:flex-row items-stretch w-full">
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

          <!-- Right: Skill Cards - FIXED OVERFLOW -->
          <div class="lg:w-2/3 border border-white/10 overflow-visible">
            <SkillCard />
          </div>
        </div>
      </div>
    </div>

    <!-- Projects Section - LED Board Style -->
    <div class="w-full bg-black">
      <div class="w-full border border-white/10 py-12 sm:py-16 md:py-20 lg:py-24 flex justify-center items-center overflow-hidden max-w-7xl mx-auto relative">
        <!-- LED Dotted Background - Enhanced -->
        <svg class="absolute inset-0 w-full h-full opacity-80" viewBox="0 0 1200 300" preserveAspectRatio="none">
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
    </div>

    <!-- Projects (Carousel Hero Style) -->
    <div class="w-full bg-black">
      <div class="max-w-7xl mx-auto">
        <ProjectCard />
      </div>
    </div>

    <!-- Work Experience Section -->
    <div class="w-full bg-black">
      <div class="border border-white/10 w-full max-w-7xl mx-auto">
        <WorkExperience />
      </div>
    </div>
  </div>

      <div class="w-full bg-black">
      <div class="border border-white/10 w-full max-w-7xl mx-auto">
        <RoleCard />
      </div>
    </div>

</template>

<script setup>
import HeroSection from '@/components/HeroSection.vue'
import SkillCard from '@/components/SkillCard.vue'
import ProjectCard from '@/components/ProjectCard.vue'
import WorkExperience from '@/components/WorkExperience.vue'
import RoleCard from '@/components/RoleCard.vue'
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

/* Blinking LED effect */
@keyframes blink {
  0%, 49% { opacity: 1; }
  50%, 100% { opacity: 0.2; }
}

.animate-blink {
  animation: blink 1s step-start infinite;
}

.glow-text {
  animation: blink 1.5s infinite;
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

/* LED flicker effect */
@keyframes flicker {
  0%, 100% { opacity: 1; }
  41% { opacity: 0.8; }
  42% { opacity: 1; }
  43% { opacity: 0.9; }
  45% { opacity: 1; }
  47% { opacity: 0.95; }
}

.animate-flicker {
  animation: flicker 5s linear infinite;
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
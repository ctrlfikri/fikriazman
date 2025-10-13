<template>
  <div class="relative w-full  min-h-[800px] overflow-hidden bg-black">
    <!-- Slides Container with SLIDING Animation -->
    <div 
      class="absolute inset-0 flex transition-transform duration-700 ease-out"
      :style="{ transform: `translateX(-${currentIndex * 100}%)` }"
    >
      <div
        v-for="(proj, index) in projects"
        :key="proj.id"
        class="relative w-full h-full flex-shrink-0"
      >
        <!-- Background Gradient -->
        <div :class="['absolute inset-0 bg-gradient-to-br', proj.bgColor]" />

        <!-- DAREIA COFFEE - Animated Coffee Bubbles -->
        <div v-if="proj.id === 1" class="absolute inset-0 overflow-hidden">
          <div
            v-for="i in 30"
            :key="`bubble-${index}-${i}`"
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

        <!-- CTRLPC - Tech Grid with Pulse -->
        <div v-if="proj.id === 2" class="absolute inset-0 overflow-hidden">
          <!-- Animated Grid Lines -->
          <div class="absolute inset-0 tech-grid opacity-30" />
          
          <!-- Scanning Lines -->
          <div class="absolute inset-0">
            <div class="absolute h-px w-full bg-gradient-to-r from-transparent via-cyan-400 to-transparent animate-scan-horizontal top-1/4" />
            <div class="absolute h-px w-full bg-gradient-to-r from-transparent via-cyan-400 to-transparent animate-scan-horizontal-delayed top-3/4" />
            <div class="absolute w-px h-full bg-gradient-to-b from-transparent via-cyan-400 to-transparent animate-scan-vertical left-1/4" />
            <div class="absolute w-px h-full bg-gradient-to-b from-transparent via-cyan-400 to-transparent animate-scan-vertical-delayed left-3/4" />
          </div>

          <!-- Glowing Nodes -->
          <div
            v-for="i in 15"
            :key="`node-${index}-${i}`"
            class="absolute w-2 h-2 bg-cyan-400 rounded-full animate-pulse-glow"
            :style="{
              left: `${Math.random() * 100}%`,
              top: `${Math.random() * 100}%`,
              animationDelay: `${Math.random() * 3}s`,
              boxShadow: '0 0 20px rgba(34, 211, 238, 0.8)',
            }"
          />
        </div>

        <!-- PROGSCALE - Code Particles & Geometric Shapes -->
        <div v-if="proj.id === 3" class="absolute inset-0 overflow-hidden">
          <!-- Floating Code Particles -->
          <div
            v-for="i in 40"
            :key="`particle-${index}-${i}`"
            class="absolute animate-code-float"
            :style="{
              left: `${Math.random() * 100}%`,
              top: `${Math.random() * 100}%`,
              animationDelay: `${Math.random() * 5}s`,
              animationDuration: `${Math.random() * 15 + 15}s`,
            }"
          >
            <div
              :class="['text-teal-600 font-mono font-bold opacity-40']"
              :style="{ fontSize: `${Math.random() * 20 + 12}px` }"
            >
              {{ ['{ }', '< >', '[ ]', '( )', '/>', '==', '=>', '++'][Math.floor(Math.random() * 8)] }}
            </div>
          </div>

          <!-- Geometric Shapes -->
          <div
            v-for="i in 8"
            :key="`geo-${index}-${i}`"
            class="absolute border-2 border-teal-500/30 animate-rotate-slow"
            :style="{
              width: `${Math.random() * 150 + 100}px`,
              height: `${Math.random() * 150 + 100}px`,
              left: `${Math.random() * 100}%`,
              top: `${Math.random() * 100}%`,
              borderRadius: Math.random() > 0.5 ? '50%' : '0%',
              animationDelay: `${Math.random() * 3}s`,
              animationDuration: `${Math.random() * 20 + 20}s`,
            }"
          />
        </div>

        <!-- Main Content Container with Arrow Space -->
        <div class="relative h-full flex items-center justify-center px-16 sm:px-20 md:px-24 lg:px-28 xl:px-32 py-8 sm:py-12 md:py-16">
          <div class="w-full max-w-7xl mx-auto">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 lg:gap-12 xl:gap-16 items-center">
              
              <!-- Text Content -->
              <div class="space-y-4 sm:space-y-6 text-center lg:text-left z-10">
                <img
                  v-if="proj.logo"
                  :src="proj.logo"
                  :alt="`${proj.name} logo`"
                  class="h-12 sm:h-16 md:h-20 lg:h-24 xl:h-28 w-auto mx-auto lg:mx-0 object-contain mb-4 drop-shadow-2xl animate-fade-in-up"
                />
                
                <h1 
                  :class="['text-4xl sm:text-5xl md:text-6xl lg:text-7xl xl:text-8xl font-black tracking-tight leading-tight animate-fade-in-up', proj.textColor, proj.fontFamily]"
                  style="animation-delay: 0.1s"
                >
                  {{ proj.name }}
                </h1>
                
                <h2 
                  :class="['text-lg sm:text-xl md:text-2xl lg:text-3xl opacity-90 font-semibold animate-fade-in-up', proj.textColor]"
                  style="animation-delay: 0.2s"
                >
                  {{ proj.role }}
                </h2>
                
                <p 
                  :class="['text-base sm:text-lg md:text-xl opacity-80 max-w-xl mx-auto lg:mx-0 leading-relaxed animate-fade-in-up', proj.textColor]"
                  style="animation-delay: 0.3s"
                >
                  {{ proj.description }}
                </p>

                <!-- Action Buttons -->
                <div class="flex flex-col sm:flex-row gap-4 pt-4 sm:pt-6 justify-center lg:justify-start animate-fade-in-up" style="animation-delay: 0.4s">
                  <a
                    :href="proj.projectLink"
                    :class="['group relative px-6 sm:px-8 py-3 sm:py-4 font-bold text-base sm:text-lg rounded-2xl shadow-xl hover:shadow-2xl transform hover:scale-105 transition-all duration-300 overflow-hidden', proj.buttonBg, proj.buttonText]"
                  >
                    <span class="relative z-10 flex items-center justify-center gap-2">
                      View Project
                      <svg class="w-5 h-5 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
                      </svg>
                    </span>
                    <div class="absolute inset-0 bg-gradient-to-r from-transparent via-white/20 to-transparent translate-x-[-200%] group-hover:translate-x-[200%] transition-transform duration-1000" />
                  </a>
                  
                  <a
                    :href="proj.socialLink"
                    target="_blank"
                    rel="noopener noreferrer"
                    :class="['px-6 sm:px-8 py-3 sm:py-4 border-3 border-current font-bold text-base sm:text-lg rounded-2xl hover:bg-white/10 backdrop-blur-sm transform hover:scale-105 transition-all duration-300 text-center', proj.textColor]"
                  >
                    Visit Link ↗
                  </a>
                </div>
              </div>

              <!-- Visual Content -->
              <div class="relative flex items-center justify-center z-10">
                <!-- Static Image -->
                <div v-if="proj.imageSrc" class="relative w-full max-w-2xl aspect-square flex items-center justify-center animate-float-smooth">
                  <img
                    :src="proj.imageSrc"
                    :alt="proj.name"
                    class="w-full h-full object-contain drop-shadow-2xl"
                  />
                </div>

                <!-- GIF Reel -->
                <div v-else-if="proj.gifs" class="relative w-full max-w-2xl h-64 sm:h-80 md:h-96 overflow-hidden rounded-3xl shadow-2xl bg-black/20 backdrop-blur-md">
                  <div class="flex h-full animate-scroll-horizontal">
                    <img
                      v-for="(gif, idx) in [...proj.gifs, ...proj.gifs]"
                      :key="`gif-${index}-${idx}`"
                      :src="gif"
                      :alt="`${proj.name} ${idx}`"
                      class="h-full w-auto object-cover flex-shrink-0 px-2"
                    />
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Navigation Buttons - Positioned Outside Content -->
    <button
      @click="prevSlide"
      :disabled="isAnimating"
      class="absolute left-2 sm:left-4 md:left-6 top-1/2 -translate-y-1/2 w-12 h-12 sm:w-14 sm:h-14 md:w-16 md:h-16 bg-white/95 hover:bg-white text-gray-900 rounded-full flex items-center justify-center shadow-2xl hover:scale-110 transition-all duration-300 disabled:opacity-50 disabled:hover:scale-100 z-50 backdrop-blur-sm"
      aria-label="Previous slide"
    >
      <svg class="w-6 h-6 sm:w-7 sm:h-7 md:w-8 md:h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
      </svg>
    </button>

    <button
      @click="nextSlide"
      :disabled="isAnimating"
      class="absolute right-2 sm:right-4 md:right-6 top-1/2 -translate-y-1/2 w-12 h-12 sm:w-14 sm:h-14 md:w-16 md:h-16 bg-white/95 hover:bg-white text-gray-900 rounded-full flex items-center justify-center shadow-2xl hover:scale-110 transition-all duration-300 disabled:opacity-50 disabled:hover:scale-100 z-50 backdrop-blur-sm"
      aria-label="Next slide"
    >
      <svg class="w-6 h-6 sm:w-7 sm:h-7 md:w-8 md:h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
      </svg>
    </button>

    <!-- Progress Indicators -->
    <div class="absolute bottom-4 sm:bottom-6 md:bottom-8 lg:bottom-12 left-1/2 -translate-x-1/2 flex items-center gap-2 sm:gap-3 z-50 bg-black/40 backdrop-blur-md px-4 sm:px-6 py-3 sm:py-4 rounded-full shadow-2xl">
      <button
        v-for="(p, index) in projects"
        :key="p.id"
        @click="goToSlide(index)"
        :disabled="isAnimating"
        :class="[
          'transition-all duration-300 rounded-full',
          currentIndex === index
            ? 'w-12 sm:w-16 md:w-20 h-2 sm:h-2.5 bg-white shadow-lg'
            : 'w-2 sm:w-2.5 h-2 sm:h-2.5 bg-white/50 hover:bg-white/70'
        ]"
        :aria-label="`Go to slide ${index + 1}`"
      />
    </div>

    <!-- Slide Counter -->
    <div class="absolute top-4 sm:top-6 md:top-8 right-4 sm:right-6 md:right-8 bg-black/40 backdrop-blur-md px-4 sm:px-6 py-2 sm:py-3 rounded-full text-white font-bold text-sm sm:text-base md:text-lg z-50 shadow-2xl">
      {{ currentIndex + 1 }} / {{ projects.length }}
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const currentIndex = ref(0)
const isAnimating = ref(false)

const projects = [
  {
    id: 1,
    name: 'Dareia Coffee',
    logo: '/dclogo.png',
    role: 'Graphic Designer & Brand Identity',
    description: 'Crafted a warm and inviting brand identity for a premium coffee experience.',
    projectLink: '#dareia',
    socialLink: 'https://instagram.com/',
    imageSrc: '/coffees.png',
    bgColor: 'from-blue-600 to-blue-800',
    textColor: 'text-white',
    buttonBg: 'bg-white',
    buttonText: 'text-blue-700',
    fontFamily: 'font-bebas',
  },
  {
    id: 2,
    name: 'CTRLPC',
    logo: '/ctrlpclogo.png',
    role: 'Content Creator & Video Editor',
    description: 'Created engaging TikTok content showcasing custom PC builds and tech reviews.',
    projectLink: '#ctrlpc',
    socialLink: 'https://tiktok.com/',
    gifs: ['/lol1.gif', '/lol2.gif', '/lol3.gif', '/lol4.gif', '/lol5.gif'],
    bgColor: 'from-cyan-500 to-teal-600',
    textColor: 'text-white',
    buttonBg: 'bg-white',
    buttonText: 'text-cyan-600',
    fontFamily: 'font-sans',
  },
  {
    id: 3,
    name: 'Progscale',
    logo: '/progscalelogo.png',
    role: 'Full Stack Developer',
    description: 'Built scalable solutions for modern web applications with cutting-edge technology.',
    projectLink: '#progscale',
    socialLink: 'https://github.com/',
    imageSrc: '/hihi.png',
    bgColor: 'from-emerald-100 to-teal-50',
    textColor: 'text-teal-900',
    buttonBg: 'bg-teal-600',
    buttonText: 'text-white',
    fontFamily: 'font-sans',
  },
]

const nextSlide = () => {
  if (isAnimating.value) return
  isAnimating.value = true
  currentIndex.value = (currentIndex.value + 1) % projects.length
  setTimeout(() => (isAnimating.value = false), 700)
}

const prevSlide = () => {
  if (isAnimating.value) return
  isAnimating.value = true
  currentIndex.value = (currentIndex.value - 1 + projects.length) % projects.length
  setTimeout(() => (isAnimating.value = false), 700)
}

const goToSlide = (index) => {
  if (isAnimating.value || index === currentIndex.value) return
  isAnimating.value = true
  currentIndex.value = index
  setTimeout(() => (isAnimating.value = false), 700)
}

const handleKeyPress = (e) => {
  if (e.key === 'ArrowLeft') prevSlide()
  if (e.key === 'ArrowRight') nextSlide()
}

onMounted(() => {
  window.addEventListener('keydown', handleKeyPress)
})

onUnmounted(() => {
  window.removeEventListener('keydown', handleKeyPress)
})
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');

.font-bebas {
  font-family: 'Bebas Neue', sans-serif;
}

/* FADE IN UP ANIMATION */
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
}

/* DAREIA - COFFEE BUBBLES FLOAT UP */
@keyframes bubble-float {
  0% {
    transform: translateY(0) scale(0.8);
    opacity: 0;
  }
  10% {
    opacity: 0.6;
  }
  90% {
    opacity: 0.4;
  }
  100% {
    transform: translateY(-120vh) scale(1.2);
    opacity: 0;
  }
}

.animate-bubble-float {
  animation: bubble-float linear infinite;
}

/* CTRLPC - TECH GRID */
.tech-grid {
  background-image: 
    linear-gradient(rgba(34, 211, 238, 0.3) 1px, transparent 1px),
    linear-gradient(90deg, rgba(34, 211, 238, 0.3) 1px, transparent 1px);
  background-size: 60px 60px;
  animation: grid-move 15s linear infinite;
}

@keyframes grid-move {
  0% { background-position: 0 0; }
  100% { background-position: 60px 60px; }
}

/* Scanning Lines */
@keyframes scan-horizontal {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(200vw); }
}

.animate-scan-horizontal {
  animation: scan-horizontal 8s linear infinite;
}

.animate-scan-horizontal-delayed {
  animation: scan-horizontal 8s linear infinite 4s;
}

@keyframes scan-vertical {
  0% { transform: translateY(-100%); }
  100% { transform: translateY(200vh); }
}

.animate-scan-vertical {
  animation: scan-vertical 10s linear infinite;
}

.animate-scan-vertical-delayed {
  animation: scan-vertical 10s linear infinite 5s;
}

/* Pulse Glow for Nodes */
@keyframes pulse-glow {
  0%, 100% {
    opacity: 0.3;
    transform: scale(1);
  }
  50% {
    opacity: 1;
    transform: scale(1.5);
  }
}

.animate-pulse-glow {
  animation: pulse-glow 2s ease-in-out infinite;
}

/* PROGSCALE - CODE PARTICLES FLOAT */
@keyframes code-float {
  0% {
    transform: translate(0, 0) rotate(0deg);
    opacity: 0;
  }
  10% {
    opacity: 0.6;
  }
  90% {
    opacity: 0.3;
  }
  100% {
    transform: translate(
      calc(-50px + ${Math.random() * 100}px),
      -100vh
    ) rotate(360deg);
    opacity: 0;
  }
}

.animate-code-float {
  animation: code-float linear infinite;
}

/* Geometric Shapes Rotation */
@keyframes rotate-slow {
  from {
    transform: rotate(0deg) scale(1);
    opacity: 0.3;
  }
  50% {
    opacity: 0.6;
  }
  to {
    transform: rotate(360deg) scale(1.2);
    opacity: 0.3;
  }
}

.animate-rotate-slow {
  animation: rotate-slow linear infinite;
}

/* IMAGE FLOAT */
@keyframes float-smooth {
  0%, 100% { 
    transform: translateY(0px) rotate(0deg); 
  }
  25% { 
    transform: translateY(-15px) rotate(1deg); 
  }
  50% { 
    transform: translateY(-25px) rotate(0deg); 
  }
  75% { 
    transform: translateY(-15px) rotate(-1deg); 
  }
}

.animate-float-smooth {
  animation: float-smooth 6s ease-in-out infinite;
}

/* GIF REEL SCROLL */
@keyframes scroll-horizontal {
  0% { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}

.animate-scroll-horizontal {
  animation: scroll-horizontal 20s linear infinite;
}
</style>

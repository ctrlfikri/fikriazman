<template>
  <div class="relative w-full h-[500px] sm:h-[600px] lg:h-[700px] overflow-hidden bg-black">
    <!-- WRAPPER -->
    <div class="relative w-full h-full overflow-hidden bg-black">
      <!-- Slides Wrapper -->
      <div class="relative w-full h-full overflow-hidden">
        <div 
          class="flex items-center h-full relative" 
          :style="{ 
            transform: `translateX(-${currentIndex * 100}%)`, 
            transition: isTransitioning ? 'transform 0.6s cubic-bezier(0.4, 0, 0.2, 1)' : 'none' 
          }"
          @transitionend="handleTransitionEnd"
        >
          <!-- Clone last slide at beginning for seamless loop -->
          <div
            class="flex-shrink-0 w-full h-full relative"
            :style="{ background: projects[projects.length - 1].bgColor, color: projects[projects.length - 1].textColor }"
          >
            <div
              v-if="projects[projects.length - 1].name === 'Dareia Coffee'"
              class="absolute inset-0 overflow-hidden z-0"
            >
              <div class="flex animate-dareia-scroll h-full opacity-60">
                <template v-for="i in 2" :key="'clone-start-bg-' + i">
                  <img
                    v-for="(img, idx) in dareiaToppings"
                    :key="img + '-clone-start-' + i + '-' + idx"
                    :src="img"
                    alt="topping"
                    class="w-[500px] object-cover flex-shrink-0 opacity-70"
                  />
                </template>
              </div>
            </div>
            <div
              v-if="projects[projects.length - 1].name === 'CTRLPC'"
              class="absolute inset-0 z-0 bg-ctrlpc-pattern"
            ></div>
            <div
              v-if="projects[projects.length - 1].name === 'Progscale'"
              class="absolute inset-0 z-0 overflow-hidden"
            >
              <div
                v-for="i in 25"
                :key="'clone-start-circle-' + i"
                class="absolute rounded-full animate-float-circle"
                :style="{
                  width: `${Math.random() * 15 + 5}px`,
                  height: `${Math.random() * 15 + 5}px`,
                  left: `${Math.random() * 100}%`,
                  top: `${Math.random() * 100}%`,
                  backgroundColor: projects[projects.length - 1].textColor,
                  opacity: Math.random() * 0.3 + 0.1,
                  animationDuration: `${Math.random() * 15 + 10}s`,
                  animationDelay: `${Math.random() * 5}s`
                }"
              ></div>
            </div>
            <div class="absolute inset-0 flex items-center justify-center px-6 sm:px-8 md:px-12 lg:px-20 xl:px-24 py-4 sm:py-6 lg:py-8 pointer-events-none overflow-hidden">
              <div class="w-full h-full max-w-[1400px] flex flex-col lg:flex-row items-center justify-center gap-6 sm:gap-8 lg:gap-16 xl:gap-20">
                <div class="relative z-10 flex justify-center items-center w-full lg:w-1/2 order-1 lg:order-2 pointer-events-auto max-h-[40%] lg:max-h-[70%]">
                  <div
                    v-if="projects[projects.length - 1].type === 'image'"
                    class="transition-all duration-700 ease-out animate-float-only w-full h-full flex items-center justify-center"
                  >
                    <img
                      :src="projects[projects.length - 1].imageSrc"
                      :alt="projects[projects.length - 1].name"
                      class="w-auto h-auto max-w-full max-h-full object-contain drop-shadow-2xl"
                    />
                  </div>
                  <div
                    v-else-if="projects[projects.length - 1].type === 'gif-reel'"
                    class="relative w-full max-w-[500px] lg:max-w-[600px] h-[200px] sm:h-[250px] lg:h-[300px] overflow-hidden shadow-2xl rounded-xl bg-black/60 backdrop-blur-sm"
                  >
                    <div class="flex animate-scroll-infinite h-full">
                      <template v-for="i in 2" :key="'clone-start-gif-loop-' + i">
                        <img
                          v-for="(gif, gifIdx) in projects[projects.length - 1].gifs"
                          :key="gif + '-clone-start-' + i + '-' + gifIdx"
                          :src="gif"
                          :alt="`${projects[projects.length - 1].name} gif ${gifIdx}`"
                          class="w-[180px] sm:w-[200px] lg:w-[240px] h-full object-cover flex-shrink-0 rounded-xl"
                        />
                      </template>
                    </div>
                  </div>
                </div>
                <div class="relative z-10 flex flex-col justify-center items-center lg:items-start text-center lg:text-left gap-3 sm:gap-4 w-full lg:w-1/2 order-2 lg:order-1 pointer-events-auto max-h-[60%] lg:max-h-full overflow-y-auto">
                  <img
                    v-if="projects[projects.length - 1].logo"
                    :src="projects[projects.length - 1].logo"
                    :alt="projects[projects.length - 1].name + ' logo'"
                    class="h-10 sm:h-12 md:h-14 lg:h-16 w-auto object-contain mb-2"
                  />
                  <h1
                    class="text-3xl sm:text-4xl md:text-5xl lg:text-6xl font-extrabold tracking-wide leading-tight break-words max-w-full"
                    :style="{ fontFamily: projects[projects.length - 1].fontFamily }"
                  >
                    {{ projects[projects.length - 1].name }}
                  </h1>
                  <h2 class="text-base sm:text-lg md:text-xl opacity-80 break-words max-w-full">
                    {{ projects[projects.length - 1].role }}
                  </h2>
                  <p class="text-sm sm:text-base md:text-lg max-w-md leading-relaxed opacity-90 break-words">
                    {{ projects[projects.length - 1].description }}
                  </p>
                  <div class="flex flex-wrap justify-center lg:justify-start gap-3 mt-2 sm:mt-3 w-full max-w-md">
                    <a
                      :href="projects[projects.length - 1].projectLink"
                      class="px-5 sm:px-6 lg:px-7 py-2.5 sm:py-3 font-semibold rounded-xl shadow-md hover:scale-105 transition-all text-sm whitespace-nowrap pointer-events-auto"
                      :style="{ backgroundColor: projects[projects.length - 1].textColor, color: projects[projects.length - 1].bgColor }"
                    >
                      View Project →
                    </a>
                    <a
                      :href="projects[projects.length - 1].socialLink"
                      target="_blank"
                      rel="noopener noreferrer"
                      class="px-5 sm:px-6 lg:px-7 py-2.5 sm:py-3 border-2 font-semibold rounded-xl hover:scale-105 transition-all text-sm whitespace-nowrap pointer-events-auto"
                      :style="{ borderColor: projects[projects.length - 1].textColor, color: projects[projects.length - 1].textColor }"
                    >
                      Visit Link ↗
                    </a>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <!-- Original slides -->          
          <div
            v-for="(project, index) in projects"
            :key="project.id"
            class="flex-shrink-0 w-full h-full relative"
            :style="{ background: project.bgColor, color: project.textColor }"
          >
            <!-- ☕ DAREIA BACKGROUND -->
            <div
              v-if="project.name === 'Dareia Coffee'"
              class="absolute inset-0 overflow-hidden z-0"
            >
              <div class="flex animate-dareia-scroll h-full opacity-60">
                <template v-for="i in 2" :key="'dareia-bg-' + index + '-' + i">
                  <img
                    v-for="(img, idx) in dareiaToppings"
                    :key="img + '-' + index + '-' + i + '-' + idx"
                    :src="img"
                    alt="topping"
                    class="w-[500px] object-cover flex-shrink-0 opacity-70"
                  />
                </template>
              </div>
            </div>

            <!-- 🖥️ CTRLPC WATERMARK BACKGROUND -->
            <div
              v-if="project.name === 'CTRLPC'"
              class="absolute inset-0 z-0 bg-ctrlpc-pattern"
            ></div>

            <!-- 🔵 PROGSCALE FLOATING CIRCLES BACKGROUND -->
            <div
              v-if="project.name === 'Progscale'"
              class="absolute inset-0 z-0 overflow-hidden"
            >
              <div
                v-for="i in 25"
                :key="'circle-' + index + '-' + i"
                class="absolute rounded-full animate-float-circle"
                :style="{
                  width: `${Math.random() * 15 + 5}px`,
                  height: `${Math.random() * 15 + 5}px`,
                  left: `${Math.random() * 100}%`,
                  top: `${Math.random() * 100}%`,
                  backgroundColor: project.textColor,
                  opacity: Math.random() * 0.3 + 0.1,
                  animationDuration: `${Math.random() * 15 + 10}s`,
                  animationDelay: `${Math.random() * 5}s`
                }"
              ></div>
            </div>

            <!-- CONTENT WRAPPER (CENTERED) -->
            <div class="absolute inset-0 flex items-center justify-center px-6 sm:px-8 md:px-12 lg:px-20 xl:px-24 py-4 sm:py-6 lg:py-8 pointer-events-none overflow-hidden">
              <div class="w-full h-full max-w-[1400px] flex flex-col lg:flex-row items-center justify-center gap-6 sm:gap-8 lg:gap-16 xl:gap-20">
                <!-- IMAGE / GIF SECTION -->
                <div class="relative z-10 flex justify-center items-center w-full lg:w-1/2 order-1 lg:order-2 pointer-events-auto max-h-[40%] lg:max-h-[70%]">
                  <!-- ☁️ Coffee Image -->
                  <div
                    v-if="project.type === 'image'"
                    class="transition-all duration-700 ease-out animate-float-only w-full h-full flex items-center justify-center"
                    :class="{
                      'opacity-100 scale-100': isAnimating,
                      'opacity-0 scale-90 translate-y-8': !isAnimating
                    }"
                  >
                    <img
                      :src="project.imageSrc"
                      :alt="project.name"
                      class="w-auto h-auto max-w-full max-h-full object-contain drop-shadow-2xl"
                    />
                  </div>

                  <!-- 🔁 Infinite GIF Reel -->
                  <div
                    v-else-if="project.type === 'gif-reel'"
                    class="relative w-full max-w-[500px] lg:max-w-[600px] h-[200px] sm:h-[250px] lg:h-[300px] overflow-hidden shadow-2xl rounded-xl bg-black/60 backdrop-blur-sm"
                  >
                    <div class="flex animate-scroll-infinite h-full">
                      <template v-for="i in 2" :key="'gif-loop-' + index + '-' + i">
                        <img
                          v-for="(gif, gifIdx) in project.gifs"
                          :key="gif + '-' + index + '-' + i + '-' + gifIdx"
                          :src="gif"
                          :alt="`${project.name} gif ${gifIdx}`"
                          class="w-[180px] sm:w-[200px] lg:w-[240px] h-full object-cover flex-shrink-0 rounded-xl"
                        />
                      </template>
                    </div>
                  </div>
                </div>

                <!-- TEXT SECTION -->
                <div class="relative z-10 flex flex-col justify-center items-center lg:items-start text-center lg:text-left gap-3 sm:gap-4 w-full lg:w-1/2 order-2 lg:order-1 pointer-events-auto max-h-[60%] lg:max-h-full overflow-y-auto">
                  <img
                    v-if="project.logo"
                    :src="project.logo"
                    :alt="project.name + ' logo'"
                    class="h-10 sm:h-12 md:h-14 lg:h-16 w-auto object-contain mb-2"
                  />

                  <h1
                    class="text-3xl sm:text-4xl md:text-5xl lg:text-6xl font-extrabold tracking-wide leading-tight break-words max-w-full"
                    :style="{ fontFamily: project.fontFamily }"
                  >
                    {{ project.name }}
                  </h1>

                  <h2 class="text-base sm:text-lg md:text-xl opacity-80 break-words max-w-full">
                    {{ project.role }}
                  </h2>

                  <p class="text-sm sm:text-base md:text-lg max-w-md leading-relaxed opacity-90 break-words">
                    {{ project.description }}
                  </p>

                  <div class="flex flex-wrap justify-center lg:justify-start gap-3 mt-2 sm:mt-3 w-full max-w-md">
                    <a
                      :href="project.projectLink"
                      class="px-5 sm:px-6 lg:px-7 py-2.5 sm:py-3 font-semibold rounded-xl shadow-md hover:scale-105 transition-all text-sm whitespace-nowrap pointer-events-auto"
                      :style="{ backgroundColor: project.textColor, color: project.bgColor }"
                    >
                      View Project →
                    </a>
                    <a
                      :href="project.socialLink"
                      target="_blank"
                      rel="noopener noreferrer"
                      class="px-5 sm:px-6 lg:px-7 py-2.5 sm:py-3 border-2 font-semibold rounded-xl hover:scale-105 transition-all text-sm whitespace-nowrap pointer-events-auto"
                      :style="{ borderColor: project.textColor, color: project.textColor }"
                    >
                      Visit Link ↗
                    </a>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <!-- Clone first slide at end for seamless loop -->
          <div
            class="flex-shrink-0 w-full h-full relative"
            :style="{ background: projects[0].bgColor, color: projects[0].textColor }"
          >
            <div
              v-if="projects[0].name === 'Dareia Coffee'"
              class="absolute inset-0 overflow-hidden z-0"
            >
              <div class="flex animate-dareia-scroll h-full opacity-60">
                <template v-for="i in 2" :key="'clone-end-bg-' + i">
                  <img
                    v-for="(img, idx) in dareiaToppings"
                    :key="img + '-clone-end-' + i + '-' + idx"
                    :src="img"
                    alt="topping"
                    class="w-[500px] object-cover flex-shrink-0 opacity-70"
                  />
                </template>
              </div>
            </div>
            <div
              v-if="projects[0].name === 'CTRLPC'"
              class="absolute inset-0 z-0 bg-ctrlpc-pattern"
            ></div>
            <div
              v-if="projects[0].name === 'Progscale'"
              class="absolute inset-0 z-0 overflow-hidden"
            >
              <div
                v-for="i in 25"
                :key="'clone-end-circle-' + i"
                class="absolute rounded-full animate-float-circle"
                :style="{
                  width: `${Math.random() * 15 + 5}px`,
                  height: `${Math.random() * 15 + 5}px`,
                  left: `${Math.random() * 100}%`,
                  top: `${Math.random() * 100}%`,
                  backgroundColor: projects[0].textColor,
                  opacity: Math.random() * 0.3 + 0.1,
                  animationDuration: `${Math.random() * 15 + 10}s`,
                  animationDelay: `${Math.random() * 5}s`
                }"
              ></div>
            </div>
            <div class="absolute inset-0 flex items-center justify-center px-6 sm:px-8 md:px-12 lg:px-20 xl:px-24 py-4 sm:py-6 lg:py-8 pointer-events-none overflow-hidden">
              <div class="w-full h-full max-w-[1400px] flex flex-col lg:flex-row items-center justify-center gap-6 sm:gap-8 lg:gap-16 xl:gap-20">
                <div class="relative z-10 flex justify-center items-center w-full lg:w-1/2 order-1 lg:order-2 pointer-events-auto max-h-[40%] lg:max-h-[70%]">
                  <div
                    v-if="projects[0].type === 'image'"
                    class="transition-all duration-700 ease-out animate-float-only w-full h-full flex items-center justify-center"
                  >
                    <img
                      :src="projects[0].imageSrc"
                      :alt="projects[0].name"
                      class="w-auto h-auto max-w-full max-h-full object-contain drop-shadow-2xl"
                    />
                  </div>
                  <div
                    v-else-if="projects[0].type === 'gif-reel'"
                    class="relative w-full max-w-[500px] lg:max-w-[600px] h-[200px] sm:h-[250px] lg:h-[300px] overflow-hidden shadow-2xl rounded-xl bg-black/60 backdrop-blur-sm"
                  >
                    <div class="flex animate-scroll-infinite h-full">
                      <template v-for="i in 2" :key="'clone-end-gif-loop-' + i">
                        <img
                          v-for="(gif, gifIdx) in projects[0].gifs"
                          :key="gif + '-clone-end-' + i + '-' + gifIdx"
                          :src="gif"
                          :alt="`${projects[0].name} gif ${gifIdx}`"
                          class="w-[180px] sm:w-[200px] lg:w-[240px] h-full object-cover flex-shrink-0 rounded-xl"
                        />
                      </template>
                    </div>
                  </div>
                </div>
                <div class="relative z-10 flex flex-col justify-center items-center lg:items-start text-center lg:text-left gap-3 sm:gap-4 w-full lg:w-1/2 order-2 lg:order-1 pointer-events-auto max-h-[60%] lg:max-h-full overflow-y-auto">
                  <img
                    v-if="projects[0].logo"
                    :src="projects[0].logo"
                    :alt="projects[0].name + ' logo'"
                    class="h-10 sm:h-12 md:h-14 lg:h-16 w-auto object-contain mb-2"
                  />
                  <h1
                    class="text-3xl sm:text-4xl md:text-5xl lg:text-6xl font-extrabold tracking-wide leading-tight break-words max-w-full"
                    :style="{ fontFamily: projects[0].fontFamily }"
                  >
                    {{ projects[0].name }}
                  </h1>
                  <h2 class="text-base sm:text-lg md:text-xl opacity-80 break-words max-w-full">
                    {{ projects[0].role }}
                  </h2>
                  <p class="text-sm sm:text-base md:text-lg max-w-md leading-relaxed opacity-90 break-words">
                    {{ projects[0].description }}
                  </p>
                  <div class="flex flex-wrap justify-center lg:justify-start gap-3 mt-2 sm:mt-3 w-full max-w-md">
                    <a
                      :href="projects[0].projectLink"
                      class="px-5 sm:px-6 lg:px-7 py-2.5 sm:py-3 font-semibold rounded-xl shadow-md hover:scale-105 transition-all text-sm whitespace-nowrap pointer-events-auto"
                      :style="{ backgroundColor: projects[0].textColor, color: projects[0].bgColor }"
                    >
                      View Project →
                    </a>
                    <a
                      :href="projects[0].socialLink"
                      target="_blank"
                      rel="noopener noreferrer"
                      class="px-5 sm:px-6 lg:px-7 py-2.5 sm:py-3 border-2 font-semibold rounded-xl hover:scale-105 transition-all text-sm whitespace-nowrap pointer-events-auto"
                      :style="{ borderColor: projects[0].textColor, color: projects[0].textColor }"
                    >
                      Visit Link ↗
                    </a>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- NAV BUTTONS -->
      <button
        @click="prevSlide"
        class="absolute top-1/2 left-2 sm:left-4 -translate-y-1/2 bg-white/90 hover:bg-white text-black w-12 h-12 sm:w-14 sm:h-14 rounded-full flex items-center justify-center text-xl sm:text-2xl z-20 shadow-lg transition-all"
      >
        ←
      </button>
      <button
        @click="nextSlide"
        class="absolute top-1/2 right-2 sm:right-4 -translate-y-1/2 bg-white/90 hover:bg-white text-black w-12 h-12 sm:w-14 sm:h-14 rounded-full flex items-center justify-center text-xl sm:text-2xl z-20 shadow-lg transition-all"
      >
        →
      </button>

      <!-- INDICATORS -->
      <div class="absolute bottom-4 sm:bottom-6 lg:bottom-8 left-1/2 -translate-x-1/2 flex gap-3 z-20">
        <button
          v-for="(p, index) in projects"
          :key="p.id"
          @click="goToSlide(index)"
          :class="[ 'h-3 rounded-full transition-all duration-300',
            (currentIndex === index + 1) || (currentIndex === 0 && index === projects.length - 1) || (currentIndex === projects.length + 1 && index === 0) ? 'bg-white w-8' : 'bg-gray-500 w-3 hover:bg-gray-400'
          ]"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch, nextTick } from 'vue'

const currentIndex = ref(1) // Start at 1 because we have a clone at 0
const isAnimating = ref(true)
const isTransitioning = ref(true)
const isSliding = ref(false) // Prevent spam clicking

const dareiaToppings = ['/1.png', '/2.png', '/3.png', '/4.png', '/5.png']

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
    type: 'image',
    bgColor: '#1a35de',
    textColor: '#ffffff',
    fontFamily: "'Bebas Neue', sans-serif",
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
    type: 'gif-reel',
    bgColor: '#01a3a5',
    textColor: '#ffffff',
    fontFamily: "'Satoshi', sans-serif",
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
    type: 'image',
    bgColor: '#cdffee',
    textColor: '#16958e',
    fontFamily: "'Satoshi', sans-serif",
  },
]

watch(currentIndex, () => {
  isAnimating.value = false
  nextTick(() => requestAnimationFrame(() => (isAnimating.value = true)))
})

function handleTransitionEnd() {
  isSliding.value = false // Allow next click
  
  // If we're at the clone of the first slide (at the end), jump to the real first slide
  if (currentIndex.value === projects.length + 1) {
    isTransitioning.value = false
    setTimeout(() => {
      currentIndex.value = 1
      setTimeout(() => {
        isTransitioning.value = true
      }, 50)
    }, 0)
  }
  // If we're at the clone of the last slide (at the beginning), jump to the real last slide
  else if (currentIndex.value === 0) {
    isTransitioning.value = false
    setTimeout(() => {
      currentIndex.value = projects.length
      setTimeout(() => {
        isTransitioning.value = true
      }, 50)
    }, 0)
  }
}

function nextSlide() {
  if (!isTransitioning.value || isSliding.value) return
  isSliding.value = true
  currentIndex.value++
}

function prevSlide() {
  if (!isTransitioning.value || isSliding.value) return
  isSliding.value = true
  currentIndex.value--
}

function goToSlide(index) {
  if (!isTransitioning.value || isSliding.value) return
  isSliding.value = true
  currentIndex.value = index + 1 // +1 because of the clone at the beginning
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Poppins:wght@900&display=swap');

/* FLOAT */
@keyframes fadeInOnce {
  from { opacity: 0; transform: translateY(20px) scale(0.98); }
  to { opacity: 1; transform: translateY(0) scale(1); }
}
@keyframes floatOnly {
  0%, 100% { transform: translateY(0); }
  50% { transform: translateY(-8px); }
}
.animate-float-only {
  animation: fadeInOnce 1s ease-out forwards, floatOnly 3s ease-in-out 1s infinite;
}

/* GIF REEL */
@keyframes scrollInfinite {
  0% { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}
.animate-scroll-infinite {
  width: 200%;
  animation: scrollInfinite 15s linear infinite;
}

/* DAREIA BG */
@keyframes dareiaScroll {
  0% { transform: translateX(0); }
  100% { transform: translateX(-50%); }
}
.animate-dareia-scroll {
  width: 200%;
  animation: dareiaScroll 40s linear infinite;
}

/* CTRLPC WATERMARK — SEAMLESS INFINITE PATTERN */
.bg-ctrlpc-pattern {
  position: absolute;
  inset: 0;
  z-index: 0;
  overflow: hidden;
  background-color: transparent;
}

.bg-ctrlpc-pattern::before,
.bg-ctrlpc-pattern::after {
  content: "CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC CTRLPC ";
  position: absolute;
  top: -100%;
  left: -100%;
  width: 500%;
  height: 500%;
  font-family: 'Poppins', sans-serif;
  font-weight: 900;
  font-size: 2.5rem;
  color: rgba(255, 255, 255, 0.08);
  line-height: 4rem;
  letter-spacing: 0.5rem;
  white-space: pre-wrap;
  word-wrap: break-word;
  pointer-events: none;
  transform: rotate(-30deg);
  animation: ctrlpcMove 100s linear infinite;
}

.bg-ctrlpc-pattern::before {
  animation-delay: -50s;
}

@keyframes ctrlpcMove {
  0% { 
    transform: rotate(-30deg) translate(0, 0); 
  }
  100% { 
    transform: rotate(-30deg) translate(-20%, -20%); 
  }
}

/* PROGSCALE FLOATING CIRCLES */
@keyframes floatCircle {
  0%, 100% {
    transform: translate(0, 0) scale(1);
    opacity: 0.2;
  }
  25% {
    transform: translate(30px, -40px) scale(1.1);
    opacity: 0.4;
  }
  50% {
    transform: translate(-20px, -80px) scale(0.9);
    opacity: 0.3;
  }
  75% {
    transform: translate(40px, -60px) scale(1.05);
    opacity: 0.35;
  }
}

.animate-float-circle {
  animation: floatCircle 20s ease-in-out infinite;
}
</style>
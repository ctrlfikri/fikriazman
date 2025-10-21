<template>
  <div class="relative py-12 sm:py-16 md:py-20 lg:py-24 overflow-hidden text-white">
    <!-- Decorative Elements -->
    <div class="absolute top-0 left-0 w-48 sm:w-72 h-48 sm:h-72 bg-orange-500/20 rounded-full blur-3xl -translate-x-1/2 -translate-y-1/2" />
    <div class="absolute bottom-0 right-0 w-64 sm:w-96 h-64 sm:h-96 bg-amber-500/20 rounded-full blur-3xl translate-x-1/2 translate-y-1/2" />

    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10">
      <!-- Make carousel appear first on mobile -->
      <div class="grid lg:grid-cols-2 gap-6 sm:gap-8 lg:gap-12 items-center">
        
        <!-- LEFT SIDE - Image Carousel -->
        <div class="relative group order-1 lg:order-1">
          <div class="relative aspect-[4/3] rounded-2xl sm:rounded-3xl overflow-hidden shadow-2xl">
            <!-- Images -->
            <div class="relative w-full h-full">
              <div
                v-for="(image, index) in carouselImages"
                :key="index"
                class="absolute inset-0 transition-opacity duration-700"
                :class="index === currentSlide ? 'opacity-100' : 'opacity-0'"
              >
                <img
                  :src="image.url"
                  :alt="image.alt"
                  class="w-full h-full object-cover"
                />
                <div class="absolute inset-0 bg-gradient-to-t from-black/50 via-transparent to-transparent" />
              </div>
            </div>

            <!-- Navigation Arrows -->
            <button
              @click="prevSlide"
              class="absolute left-2 sm:left-4 top-1/2 -translate-y-1/2 w-10 h-10 sm:w-12 sm:h-12 bg-white/90 backdrop-blur-sm rounded-full flex items-center justify-center shadow-lg opacity-0 group-hover:opacity-100 transition-opacity hover:bg-white hover:scale-110 transform duration-200"
              aria-label="Previous image"
            >
              <svg class="w-5 h-5 sm:w-6 sm:h-6 text-gray-800" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
              </svg>
            </button>
            <button
              @click="nextSlide"
              class="absolute right-2 sm:right-4 top-1/2 -translate-y-1/2 w-10 h-10 sm:w-12 sm:h-12 bg-white/90 backdrop-blur-sm rounded-full flex items-center justify-center shadow-lg opacity-0 group-hover:opacity-100 transition-opacity hover:bg-white hover:scale-110 transform duration-200"
              aria-label="Next image"
            >
              <svg class="w-5 h-5 sm:w-6 sm:h-6 text-gray-800" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
              </svg>
            </button>

            <!-- Dot Indicators -->
            <div class="absolute bottom-4 sm:bottom-6 left-1/2 -translate-x-1/2 flex gap-1.5 sm:gap-2">
              <button
                v-for="(_, index) in carouselImages"
                :key="index"
                @click="goToSlide(index)"
                class="transition-all duration-300 rounded-full"
                :class="index === currentSlide ? 'w-6 sm:w-8 h-1.5 sm:h-2 bg-white' : 'w-1.5 sm:w-2 h-1.5 sm:h-2 bg-white/50 hover:bg-white/75'"
                :aria-label="`Go to slide ${index + 1}`"
              />
            </div>
          </div>
        </div>

        <!-- RIGHT SIDE - CTA Content -->
        <div class="space-y-6 sm:space-y-8 order-2 lg:order-2 text-white">
          <!-- Badge -->
          <div class="inline-flex items-center gap-2 bg-white/10 backdrop-blur-sm px-3 sm:px-4 py-2 rounded-full text-xs sm:text-sm font-semibold border border-white/20">
            <span class="w-2 h-2 bg-orange-400 rounded-full animate-pulse" />
            Final Showcase
          </div>

          <!-- Heading -->
          <div class="space-y-3 sm:space-y-4">
            <h2 class="text-3xl sm:text-4xl md:text-5xl lg:text-6xl font-black leading-tight">
              More than<br />
              <span class="bg-gradient-to-r from-orange-300 to-amber-300 bg-clip-text text-transparent">
                just Coffee
              </span>
            </h2>
            <p class="text-base sm:text-lg md:text-xl text-white/80 leading-relaxed max-w-xl">
              While you're at it, follow Dareia Coffee on social media to stay updated with the latest offerings, promotions, and community events.
            </p>
          </div>

          <!-- Social Media Buttons -->
          <div class="flex flex-col sm:flex-row gap-3 sm:gap-4 pt-2 sm:pt-4">
            <!-- Instagram -->
            <a
              href="https://instagram.com/dareiacoffeepenang"
              target="_blank"
              rel="noopener noreferrer"
              class="group relative px-6 sm:px-8 py-3.5 sm:py-4 bg-gradient-to-br from-purple-500 via-pink-500 to-orange-500 text-white font-bold text-base sm:text-lg rounded-xl sm:rounded-2xl shadow-lg hover:shadow-pink-500/50 transform hover:scale-105 transition-all duration-300 overflow-hidden"
            >
              <span class="relative z-10 flex items-center justify-center gap-2 sm:gap-3">
                <svg class="w-5 h-5 sm:w-6 sm:h-6" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M12 2.163c3.204 0 3.584.012 4.85.07..." />
                </svg>
                Instagram
              </span>
              <div class="absolute inset-0 bg-gradient-to-r from-transparent via-white/30 to-transparent translate-x-[-200%] group-hover:translate-x-[200%] transition-transform duration-1000" />
            </a>

            <!-- TikTok -->
            <a
              href="https://tiktok.com/@dareiacoffeepenang"
              target="_blank"
              rel="noopener noreferrer"
              class="group relative px-6 sm:px-8 py-3.5 sm:py-4 bg-black text-white font-bold text-base sm:text-lg rounded-xl sm:rounded-2xl shadow-lg hover:shadow-black/50 transform hover:scale-105 transition-all duration-300 overflow-hidden border-2 border-white/20"
            >
              <span class="relative z-10 flex items-center justify-center gap-2 sm:gap-3">
                <svg class="w-5 h-5 sm:w-6 sm:h-6" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M19.59 6.69a4.83 4.83..." />
                </svg>
                TikTok
              </span>
            </a>

            <!-- Facebook -->
            <a
              href="https://facebook.com/dareiacoffeepenang"
              target="_blank"
              rel="noopener noreferrer"
              class="group relative px-6 sm:px-8 py-3.5 sm:py-4 bg-blue-600 text-white font-bold text-base sm:text-lg rounded-xl sm:rounded-2xl shadow-lg hover:shadow-blue-500/50 transform hover:scale-105 transition-all duration-300 overflow-hidden"
            >
              <span class="relative z-10 flex items-center justify-center gap-2 sm:gap-3">
                <svg class="w-5 h-5 sm:w-6 sm:h-6" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M24 12.073c0-6.627-5.373-12..." />
                </svg>
                Facebook
              </span>
            </a>
          </div>

          <!-- Stats Row -->
          <div class="grid grid-cols-3 gap-4 sm:gap-6 pt-6 sm:pt-8 border-t border-white/20">
            <div class="text-center">
              <div class="text-2xl sm:text-3xl font-bold">10K+</div>
              <div class="text-xs sm:text-sm text-white/70 mt-1">Followers</div>
            </div>
            <div class="text-center">
              <div class="text-2xl sm:text-3xl font-bold">20+</div>
              <div class="text-xs sm:text-sm text-white/70 mt-1">Reviews</div>
            </div>
            <div class="text-center">
              <div class="text-2xl sm:text-3xl font-bold">5★</div>
              <div class="text-xs sm:text-sm text-white/70 mt-1">Rating</div>
            </div>
          </div>
        </div>

      </div>
    </div>

    <!-- Bottom Footer -->
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 relative z-10 mt-16 pt-8 border-t border-white/20">
      <div class="flex flex-col sm:flex-row justify-between items-center gap-4 text-sm text-white/70">
        <p>© 2024 Dareia Coffee. All rights reserved.</p>
        <p>Template & Design by <span class="text-white font-semibold">Fikri Azman</span></p>
        <a
          href="#hero"
          class="inline-flex items-center gap-2 text-white/70 hover:text-white font-semibold transition-colors group"
        >
          <svg class="w-5 h-5 group-hover:-translate-y-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 10l7-7m0 0l7 7m-7-7v18" />
          </svg>
          Back to Top
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const currentSlide = ref(0)
const isAutoPlaying = ref(true)
let intervalId = null

const carouselImages = [
  { url: '/crsl-1.jpeg', alt: 'menu panel' },
  { url: '/crsl-2.png', alt: 'voucher' },
  { url: '/crsl-3.jpg', alt: 'vertical banner' },
  { url: '/banner.jpg', alt: 'horizontal banner' }
]

const nextSlide = () => currentSlide.value = (currentSlide.value + 1) % carouselImages.length
const prevSlide = () => currentSlide.value = (currentSlide.value - 1 + carouselImages.length) % carouselImages.length
const goToSlide = (i) => { currentSlide.value = i; isAutoPlaying.value = false; if (intervalId) clearInterval(intervalId) }

onMounted(() => {
  intervalId = setInterval(() => { if (isAutoPlaying.value) nextSlide() }, 4000)
})

onUnmounted(() => { if (intervalId) clearInterval(intervalId) })
</script>

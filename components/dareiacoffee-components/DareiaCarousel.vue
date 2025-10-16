<template>
  <div class="relative py-16 sm:py-20 md:py-24 lg:py-32 px-4 sm:px-6 lg:px-8 bg-white/5 backdrop-blur-sm overflow-hidden">
    <div class="max-w-7xl mx-auto">
      
      <!-- Section Header -->
      <div class="text-center mb-12 sm:mb-16 space-y-4 sm:space-y-6">
        <div class="inline-block px-4 py-2 bg-white/20 backdrop-blur-sm rounded-full">
          <p class="text-white/90 font-semibold text-sm sm:text-base">Social Media</p>
        </div>
        
        <h2 class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-black text-white leading-tight">
          Content Gallery
        </h2>
        
        <p class="text-white/80 text-base sm:text-lg md:text-xl max-w-2xl mx-auto">
          Explore the visual stories I created for Dareia Coffee's social media presence
        </p>
      </div>

      <!-- Infinite Carousel -->
      <div class="relative">
        <!-- Gradient Overlays -->
        <div class="absolute left-0 top-0 bottom-0 w-20 sm:w-32 md:w-40 bg-gradient-to-r from-blue-700 to-transparent z-10 pointer-events-none" />
        <div class="absolute right-0 top-0 bottom-0 w-20 sm:w-32 md:w-40 bg-gradient-to-l from-blue-800 to-transparent z-10 pointer-events-none" />

        <!-- Scrolling Container -->
        <div class="overflow-hidden">
          <div 
            class="flex gap-4 sm:gap-6 md:gap-8"
            :class="{ 'animate-scroll-infinite': !isPaused }"
            @mouseenter="pauseScroll"
            @mouseleave="resumeScroll"
          >
            <!-- First Set of Images -->
            <div
              v-for="(post, index) in [...socialPosts, ...socialPosts]"
              :key="`post-${index}`"
              class="flex-shrink-0 group cursor-pointer"
            >
              <div class="relative w-64 h-64 sm:w-72 sm:h-72 md:w-80 md:h-80 lg:w-96 lg:h-96 rounded-2xl overflow-hidden shadow-2xl transform transition-all duration-500 hover:scale-105 hover:shadow-white/20">
                <!-- Actual Image -->
                <img
                  :src="post.image"
                  :alt="post.title"
                  class="w-full h-full object-cover"
                />

                <!-- Hover Overlay -->
                <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-black/40 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-end p-4 sm:p-6">
                  <div>
                    <p class="text-white font-bold text-base sm:text-lg mb-1">{{ post.title }}</p>
                    <p class="text-white/80 text-xs sm:text-sm">{{ post.description }}</p>
                  </div>
                </div>

                <!-- Instagram Icon Badge -->
                <div class="absolute top-3 right-3 sm:top-4 sm:right-4 w-8 h-8 sm:w-10 sm:h-10 bg-gradient-to-br from-purple-500 via-pink-500 to-orange-500 rounded-xl flex items-center justify-center shadow-lg opacity-90 group-hover:opacity-100 transition-opacity">
                  <svg class="w-5 h-5 sm:w-6 sm:h-6 text-white" fill="currentColor" viewBox="0 0 24 24">
                    <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
                  </svg>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- View More Button -->
      <div class="text-center mt-12 sm:mt-16">
        <a
          href="https://instagram.com/dareiacoffee"
          target="_blank"
          rel="noopener noreferrer"
          class="inline-flex items-center gap-3 px-8 sm:px-10 py-4 sm:py-5 bg-white text-blue-700 font-bold text-base sm:text-lg rounded-2xl shadow-2xl hover:shadow-white/30 transform hover:scale-105 transition-all duration-300"
        >
          <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
            <path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/>
          </svg>
          See More on Instagram
        </a>
      </div>

    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const isPaused = ref(false)

const socialPosts = [
  { id: 1, title: 'New Menu Launch', description: 'Announcing our refreshed menu', image: '/1.webp' },
  { id: 2, title: 'Coffee of the Week', description: 'Featured blend showcase', image: '/2.webp' },
  { id: 3, title: 'Promo Campaign', description: 'Special discount announcement', image: '/3.webp' },
  { id: 4, title: 'Behind the Beans', description: 'Coffee sourcing story', image: '/4.webp' },
  { id: 5, title: 'Customer Spotlight', description: 'Community appreciation post', image: '/5.webp' },
  { id: 6, title: 'Seasonal Special', description: 'Limited time offering', image: '/6.webp' },
  { id: 7, title: 'Barista Tips', description: 'Coffee brewing guide', image: '/7.webp' },
]

const pauseScroll = () => {
  isPaused.value = true
}

const resumeScroll = () => {
  isPaused.value = false
}
</script>

<style scoped>
/* Infinite Scroll Animation */
@keyframes scroll-infinite {
  0% {
    transform: translateX(0);
  }
  100% {
    transform: translateX(-50%);
  }
}

.animate-scroll-infinite {
  animation: scroll-infinite 40s linear infinite;
}

.animate-scroll-infinite:hover {
  animation-play-state: paused;
}
</style>
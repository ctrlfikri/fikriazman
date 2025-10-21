<script setup>
import { ref } from 'vue'
import BentoItem from './BentoItem.vue'

const currentSlide = ref(0)

const campaigns = [
  {
    id: 1,
    title: 'Ramadan Promo',
    icon: '🌙',
    description: 'Special promotional campaign celebrating Ramadan',
    duration: '1 Month',
    platforms: 'IG, FB, TikTok',
    objective: 'Increase traffic',
    images: {
      ultraWide: '/horizontal banner-1.webp', // 2.5:1 ratio
      square1: '/ramadan-1.webp',
      square2: '/ramadan-2.webp',
      a2: '/vertical banner-1.webp' // 5:7 ratio
    }
  },
  {
    id: 2,
    title: 'Grand Opening',
    icon: '🎉',
    description: 'Launch campaign introducing Dareia Coffee',
    duration: '2 Weeks',
    platforms: 'IG, FB',
    objective: 'Brand awareness',
    images: {
      ultraWide: '/horizontal banner-2.webp',
      square1: '/mednes-1.webp',
      square2: '/mednes-2.webp',
      a2: '/vertical banner-2.webp'
    }
  },
  {
    id: 3,
    title: 'Summer Special',
    icon: '☀️',
    description: 'Refreshing summer campaign with seasonal menu',
    duration: '3 Months',
    platforms: 'IG, TikTok',
    objective: 'Seasonal sales',
    images: {
      ultraWide: '/horizontal banner-3.webp',
      square1: '/mffn-1.webp',
      square2: '/path/to/summer-square2.jpg',
      a2: '/vertical banner-3.webp'
    }
  }
]

// Carousel Controls
const nextSlide = () => {
  if (currentSlide.value < campaigns.length - 1) currentSlide.value++
}
const prevSlide = () => {
  if (currentSlide.value > 0) currentSlide.value--
}
const goToSlide = (index) => {
  currentSlide.value = index
}
</script>

<template>
  <div class="relative py-8 sm:py-12 md:py-16 lg:py-20 px-4 sm:px-6 lg:px-8">
    <div class="max-w-7xl mx-auto">

      <!-- Header -->
      <div class="text-center mb-8 sm:mb-12 space-y-3 sm:space-y-4">
        <div class="inline-block px-3 sm:px-4 py-2 bg-white/20 backdrop-blur-sm rounded-full">
          <p class="text-white/90 font-semibold text-sm sm:text-base">Visual Campaigns</p>
        </div>
        <h2 class="text-3xl sm:text-4xl md:text-5xl lg:text-6xl font-black text-white leading-tight">
          Promotional<br class="sm:hidden" /> Materials
        </h2>
        <p class="text-white/80 text-sm sm:text-base md:text-lg max-w-2xl mx-auto">
          Explore the complete range of promotional materials for each campaign
        </p>
      </div>

      <!-- Carousel -->
      <div class="relative overflow-hidden rounded-2xl bg-gradient-to-b from-transparent to-black/10 p-4 sm:p-6">
        <div
          class="flex transition-transform duration-700 ease-out w-full"
          :style="{ transform: `translateX(-${currentSlide * 100}%)` }"
        >
          <div
            v-for="campaign in campaigns"
            :key="campaign.id"
            class="min-w-full flex-shrink-0 px-2 sm:px-4 flex flex-col"
          >
            <!-- Campaign Header -->
            <div class="text-center mb-4 sm:mb-6">
              <div class="inline-flex items-center gap-2 sm:gap-3 bg-white/10 backdrop-blur-md rounded-xl sm:rounded-2xl px-3 sm:px-4 py-2.5 sm:py-3 border border-white/20 max-w-md mx-auto">
                <div class="w-8 h-8 sm:w-10 sm:h-10 bg-gradient-to-br from-yellow-400 to-orange-500 rounded-lg sm:rounded-xl flex items-center justify-center flex-shrink-0">
                  <span class="text-lg sm:text-xl">{{ campaign.icon }}</span>
                </div>
                <div class="text-left min-w-0">
                  <h3 class="text-lg sm:text-xl md:text-2xl font-black text-white truncate">{{ campaign.title }}</h3>
                  <p class="text-white/70 text-xs sm:text-sm line-clamp-2">{{ campaign.description }}</p>
                </div>
              </div>
            </div>

            <!-- Bento Grid Container -->
            <div class="max-w-5xl mx-auto mb-6">
              <!-- Bento Grid - Ultra Wide + A2 Portrait Layout -->
              <div class="grid grid-cols-1 lg:grid-cols-5 gap-3 sm:gap-4 lg:h-[480px]">
                
                <!-- Left Column: 3/5 width -->
                <div class="lg:col-span-3 flex flex-col gap-3 sm:gap-4 h-full">
                  <!-- Ultra Wide Banner (2.5:1) - Takes 50% of height -->
                  <div class="flex-[5]">
                    <BentoItem 
                      type="ultrawide" 
                      label="Ultra Wide Banner (18000x7200)"
                      :imageUrl="campaign.images?.ultraWide"
                    />
                  </div>
                  
                  <!-- Two Square Posts - Takes 50% of height -->
                  <div class="flex-[5] grid grid-cols-2 gap-3 sm:gap-4">
                    <BentoItem 
                      type="square" 
                      label="Square Post (1080x1080)"
                      :imageUrl="campaign.images?.square1"
                    />
                    <BentoItem 
                      type="square" 
                      label="Square Post (1080x1080)"
                      :imageUrl="campaign.images?.square2"
                    />
                  </div>
                </div>

                <!-- Right Column: 2/5 width, full height for A2 -->
                <div class="lg:col-span-2 h-full lg:min-h-0 min-h-[500px]">
                  <BentoItem 
                    type="a2" 
                    label="A2 Poster (420x594mm)"
                    :imageUrl="campaign.images?.a2"
                  />
                </div>
              </div>
            </div>

            <!-- Campaign Stats -->
            <div class="max-w-5xl mx-auto p-3 sm:p-4 bg-white/10 backdrop-blur-md rounded-xl border border-white/20">
              <div class="grid grid-cols-2 sm:grid-cols-4 gap-2 sm:gap-3 text-center">
                <div><p class="text-white/60 text-xs mb-1">Duration</p><p class="text-white font-bold text-xs sm:text-sm">{{ campaign.duration }}</p></div>
                <div><p class="text-white/60 text-xs mb-1">Platforms</p><p class="text-white font-bold text-xs sm:text-sm">{{ campaign.platforms }}</p></div>
                <div><p class="text-white/60 text-xs mb-1">Assets</p><p class="text-white font-bold text-xs sm:text-sm">4 Designs</p></div>
                <div><p class="text-white/60 text-xs mb-1">Objective</p><p class="text-white font-bold text-xs sm:text-sm">{{ campaign.objective }}</p></div>
              </div>
            </div>
          </div>
        </div>

        <!-- Navigation -->
        <button @click="prevSlide" :disabled="currentSlide === 0" class="absolute left-2 sm:left-4 top-1/2 -translate-y-1/2 w-10 h-10 sm:w-12 sm:h-12 bg-white hover:bg-white/90 text-blue-700 rounded-full flex items-center justify-center shadow-lg hover:scale-105 transition-all duration-200 disabled:opacity-30 disabled:cursor-not-allowed z-10">
          <svg class="w-5 h-5 sm:w-6 sm:h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"/></svg>
        </button>
        <button @click="nextSlide" :disabled="currentSlide === campaigns.length-1" class="absolute right-2 sm:right-4 top-1/2 -translate-y-1/2 w-10 h-10 sm:w-12 sm:h-12 bg-white hover:bg-white/90 text-blue-700 rounded-full flex items-center justify-center shadow-lg hover:scale-105 transition-all duration-200 disabled:opacity-30 disabled:cursor-not-allowed z-10">
          <svg class="w-5 h-5 sm:w-6 sm:h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"/></svg>
        </button>

        <!-- Dots -->
        <div class="flex justify-center gap-2 mt-6 sm:mt-8">
          <button
            v-for="(campaign, index) in campaigns"
            :key="campaign.id"
            @click="goToSlide(index)"
            :class="[
              'transition-all duration-300 rounded-full',
              currentSlide === index ? 'w-8 sm:w-12 h-1.5 sm:h-2 bg-white shadow-md' : 'w-1.5 sm:w-2 h-1.5 sm:h-2 bg-white/50 hover:bg-white/70'
            ]"
            :aria-label="`Go to ${campaign.title}`"
          />
        </div>

        <!-- Counter -->
        <div class="text-center mt-3 sm:mt-4">
          <p class="text-white/70 text-sm font-semibold">{{ currentSlide+1 }} / {{ campaigns.length }}</p>
        </div>
      </div>
    </div>
  </div>
</template>
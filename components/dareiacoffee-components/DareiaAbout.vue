<template>
  <div class="relative py-16 sm:py-20 md:py-24 lg:py-32 px-4 sm:px-6 lg:px-8">
    <div class="max-w-7xl mx-auto">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 lg:gap-12 xl:gap-16 items-center">
        
        <!-- Text Content -->
        <div class="space-y-6 sm:space-y-8 order-2 lg:order-1">
          <div class="inline-block px-4 py-2 bg-white/20 backdrop-blur-sm rounded-full">
            <p class="text-white/90 font-semibold text-sm sm:text-base">About Dareia Coffee</p>
          </div>

          <h2 class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-black text-white leading-tight">
            Where Coffee<br />Meets Community
          </h2>

          <div class="space-y-4 text-white/80 text-base sm:text-lg md:text-xl leading-relaxed">
            <p>
              Dareia Coffee is more than just a café — it's a sanctuary for coffee lovers seeking authentic experiences and genuine connections. Nestled in the heart of the community, we pride ourselves on serving premium, ethically-sourced coffee with warmth and hospitality.
            </p>
            <p>
              From the first sip to the last, every moment at Dareia Coffee is designed to be memorable. Our cozy ambiance, paired with expertly crafted beverages, creates the perfect backdrop for conversations, creativity, and comfort.
            </p>
            <p class="font-semibold text-white">
              This is where your coffee story begins. ☕
            </p>
          </div>

          <div class="grid grid-cols-2 sm:grid-cols-3 gap-4 sm:gap-6 pt-6">
            <div class="text-center lg:text-left">
              <p class="text-3xl sm:text-4xl md:text-5xl font-black text-white">5+</p>
              <p class="text-white/70 text-sm sm:text-base mt-1">Years Serving</p>
            </div>
            <div class="text-center lg:text-left">
              <p class="text-3xl sm:text-4xl md:text-5xl font-black text-white">50+</p>
              <p class="text-white/70 text-sm sm:text-base mt-1">Menu Items</p>
            </div>
            <div class="text-center lg:text-left col-span-2 sm:col-span-1">
              <p class="text-3xl sm:text-4xl md:text-5xl font-black text-white">10k+</p>
              <p class="text-white/70 text-sm sm:text-base mt-1">Happy Customers</p>
            </div>
          </div>
        </div>

        <!-- Image -->
        <div class="order-1 lg:order-2 relative">
          <!-- Outer wrapper so badge isn't clipped -->
          <div class="relative inline-block">
            <!-- Image Container -->
            <div class="relative rounded-3xl overflow-hidden shadow-2xl transform hover:scale-105 transition-transform duration-500">
              <div class="aspect-[4/5] bg-white/10 backdrop-blur-sm flex items-center justify-center">
                <img 
                  src="/cafe.png" 
                  alt="Cafe Interior"
                  class="w-full h-full object-cover"
                />
              </div>
              <!-- Decorative Border -->
              <div class="absolute inset-0 border-4 border-white/20 rounded-3xl pointer-events-none"></div>
            </div>

            <!-- Floating Badge (outside overflow-hidden) -->
            <div class="absolute -top-4 -right-4 sm:-top-6 sm:-right-6 bg-white text-blue-700 px-4 sm:px-6 py-3 sm:py-4 rounded-2xl shadow-2xl transform rotate-6 hover:rotate-0 transition-transform duration-300">
              <p class="font-black text-lg sm:text-xl md:text-2xl">Est. 2019</p>
            </div>
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script setup>
// Static content component
</script>

<style scoped>
/* optional gentle float animation for the badge */
@keyframes float {
  0%, 100% { transform: translateY(0) rotate(6deg); }
  50% { transform: translateY(-4px) rotate(5deg); }
}
.badge-float {
  animation: float 4s ease-in-out infinite;
}
</style>

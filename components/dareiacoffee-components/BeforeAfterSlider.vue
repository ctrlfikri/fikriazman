<template>
  <div class="relative py-16 sm:py-20 md:py-24 lg:py-32 px-4 sm:px-6 lg:px-8 ">
    <div class="max-w-6xl mx-auto">
      
      <!-- Section Header -->
      <div class="text-center mb-12 sm:mb-16 space-y-4 sm:space-y-6">
        <div class="inline-block px-4 py-2 bg-white/20 backdrop-blur-sm rounded-full">
          <p class="text-white/90 font-semibold text-sm sm:text-base">Transformation</p>
        </div>
        
        <h2 class="text-4xl sm:text-5xl md:text-6xl lg:text-7xl font-black text-white leading-tight">
          Before & After
        </h2>
        
        <p class="text-white/80 text-base sm:text-lg md:text-xl max-w-2xl mx-auto">
          Drag the slider to see how I transformed Dareia Coffee's menu design
        </p>
      </div>

      <!-- Before/After Slider Container -->
      <div class="relative w-full flex justify-center">
        <div 
          ref="containerRef"
          class="relative h-[70vh] sm:h-[75vh] md:h-[80vh] bg-gray-50 cursor-ew-resize select-none rounded-2xl overflow-hidden shadow-2xl"
          style="aspect-ratio: 1/1.414; width: auto; max-width: 100%;"
          @mousedown="startDragging"
          @touchstart="startDragging"
        >
          <!-- BEFORE Image (Left Side - Base Layer) -->
          <div class="absolute inset-0">
            <img
              src="/before-menu.webp"
              alt="Old Menu Panel - Before Redesign"
              class="w-full h-full object-contain"
            />
            <div class="absolute top-4 left-4 sm:top-6 sm:left-6 z-10 bg-red-500/90 backdrop-blur-sm px-4 sm:px-6 py-2 sm:py-3 rounded-full shadow-xl">
              <p class="text-white font-bold text-sm sm:text-base">BEFORE</p>
            </div>
          </div>

          <!-- AFTER Image (Right Side - Reveals as slider moves right) -->
          <div 
            class="absolute inset-0 overflow-hidden"
            :style="{ clipPath: `inset(0 0 0 ${sliderPosition}%)` }"
          >
            <img
              src="/after-menu.webp"
              alt="New Menu Panel - After Redesign"
              class="w-full h-full object-cover"
            />
            <div class="absolute top-4 right-4 sm:top-6 sm:right-6 z-10 bg-green-500/90 backdrop-blur-sm px-4 sm:px-6 py-2 sm:py-3 rounded-full shadow-xl">
              <p class="text-white font-bold text-sm sm:text-base">AFTER</p>
            </div>
          </div>

          <!-- Slider Handle -->
          <div 
            class="absolute top-0 bottom-0 w-1 bg-white shadow-2xl z-20 cursor-ew-resize"
            :style="{ left: `${sliderPosition}%` }"
          >
            <!-- Handle Circle -->
            <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-12 h-12 sm:w-16 sm:h-16 bg-white rounded-full shadow-2xl flex items-center justify-center ring-4 ring-blue-600/30">
              <div class="flex gap-1">
                <svg class="w-4 h-4 sm:w-5 sm:h-5 text-blue-600" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M12.707 5.293a1 1 0 010 1.414L9.414 10l3.293 3.293a1 1 0 01-1.414 1.414l-4-4a1 1 0 010-1.414l4-4a1 1 0 011.414 0z" clip-rule="evenodd" />
                </svg>
                <svg class="w-4 h-4 sm:w-5 sm:h-5 text-blue-600" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M7.293 14.707a1 1 0 010-1.414L10.586 10 7.293 6.707a1 1 0 011.414-1.414l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414 0z" clip-rule="evenodd" />
                </svg>
              </div>
            </div>
          </div>
        </div>

        <!-- Instructions -->
        <div class="absolute bottom-4 left-1/2 -translate-x-1/2 bg-black/60 backdrop-blur-md px-4 sm:px-6 py-2 sm:py-3 rounded-full text-white text-xs sm:text-sm font-semibold z-30 pointer-events-none shadow-xl">
          👆 Drag to compare
        </div>
      </div>

      <!-- Stats Below Slider -->
      <div class="mt-12 sm:mt-16 grid grid-cols-1 sm:grid-cols-3 gap-6 sm:gap-8">
        <div class="text-center bg-white/10 backdrop-blur-md rounded-2xl p-6 sm:p-8 border border-white/20">
          <p class="text-4xl sm:text-5xl font-black text-white mb-2">150%</p>
          <p class="text-white/80 text-sm sm:text-base">Increase in Menu Clarity</p>
        </div>
        <div class="text-center bg-white/10 backdrop-blur-md rounded-2xl p-6 sm:p-8 border border-white/20">
          <p class="text-4xl sm:text-5xl font-black text-white mb-2">Modern</p>
          <p class="text-white/80 text-sm sm:text-base">Visual Appeal</p>
        </div>
        <div class="text-center bg-white/10 backdrop-blur-md rounded-2xl p-6 sm:p-8 border border-white/20">
          <p class="text-4xl sm:text-5xl font-black text-white mb-2">100%</p>
          <p class="text-white/80 text-sm sm:text-base">Brand Consistency</p>
        </div>
      </div>

    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const containerRef = ref(null)
const sliderPosition = ref(50) // Start at 50% (middle)
const isDragging = ref(false)

const updateSliderPosition = (clientX) => {
  if (!containerRef.value) return
  
  const rect = containerRef.value.getBoundingClientRect()
  const x = clientX - rect.left
  const percentage = (x / rect.width) * 100
  
  // Clamp between 0 and 100
  sliderPosition.value = Math.max(0, Math.min(100, percentage))
}

const startDragging = (e) => {
  isDragging.value = true
  const clientX = e.type.includes('mouse') ? e.clientX : e.touches[0].clientX
  updateSliderPosition(clientX)
}

const onDrag = (e) => {
  if (!isDragging.value) return
  const clientX = e.type.includes('mouse') ? e.clientX : e.touches[0].clientX
  updateSliderPosition(clientX)
}

const stopDragging = () => {
  isDragging.value = false
}

onMounted(() => {
  document.addEventListener('mousemove', onDrag)
  document.addEventListener('mouseup', stopDragging)
  document.addEventListener('touchmove', onDrag)
  document.addEventListener('touchend', stopDragging)
})

onUnmounted(() => {
  document.removeEventListener('mousemove', onDrag)
  document.removeEventListener('mouseup', stopDragging)
  document.removeEventListener('touchmove', onDrag)
  document.removeEventListener('touchend', stopDragging)
})
</script>

<style scoped>
/* Prevent text selection while dragging */
.select-none {
  user-select: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
}
</style>
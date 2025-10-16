<script setup>
import { computed } from 'vue'

// Props for BentoItem
const props = defineProps({
  label: { type: String, required: true },
  type: { type: String, default: 'square' },
  imageUrl: { type: String, default: null }
})

// Compute the aspect class for the inner content
const aspectClass = computed(() => {
  switch (props.type) {
    case 'ultrawide':
      return 'aspect-[5/2]' // 2.5:1 ratio for 18000x7200
    case 'a2':
      return 'aspect-[5/7]' // A2 ratio (420x594mm)
    case 'square':
    default:
      return 'aspect-square' // 1:1
  }
})
</script>

<template>
  <div
    class="bg-white/10 backdrop-blur-md rounded-xl p-2 sm:p-3 border border-white/20 w-full h-full flex items-center justify-center"
  >
    <div
      :class="[
        'max-w-full max-h-full rounded-lg overflow-hidden shadow-lg relative group',
        aspectClass
      ]"
    >
      <!-- Image Preview -->
      <img 
        v-if="imageUrl" 
        :src="imageUrl" 
        :alt="label"
        class="w-full h-full object-contain bg-gray-100"
      />
      
      <!-- Placeholder with label -->
      <div 
        v-else
        class="w-full h-full bg-gradient-to-br from-gray-100 to-gray-200 flex items-center justify-center text-gray-400"
      >
        <div class="text-center px-2">
          <svg class="w-8 h-8 sm:w-12 sm:h-12 mx-auto mb-2 opacity-50" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z" />
          </svg>
          <p class="text-xs sm:text-sm font-medium">{{ label }}</p>
        </div>
      </div>

      <!-- Hover Overlay with Label -->
      <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-black/20 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-end justify-center p-2 sm:p-3">
        <p class="text-white text-xs sm:text-sm font-semibold text-center">{{ label }}</p>
      </div>
    </div>
  </div>
</template>
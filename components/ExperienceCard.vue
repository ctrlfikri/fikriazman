<template>
  <div 
    :class="[
      'relative w-full h-full rounded-lg transition-all duration-500',
      isActive ? 'shadow-2xl shadow-white/10' : 'shadow-lg',
    ]"
  >
    <!-- BLANK STATE (Default) -->
    <div 
      v-if="showMode === 'blank'"
      class="absolute inset-0 bg-gradient-to-br from-white/10 to-white/5 backdrop-blur-sm border-2 border-white/20 rounded-lg flex items-center justify-center overflow-hidden"
    >
      <!-- Subtle pattern on card back -->
      <div class="absolute inset-0 opacity-5" 
           style="background-image: repeating-linear-gradient(45deg, transparent, transparent 10px, rgba(255,255,255,0.1) 10px, rgba(255,255,255,0.1) 20px);">
      </div>
      
      <!-- Center logo/text -->
      <div class="relative z-10 text-center">
        <div class="text-6xl font-bold text-white/20 font-mono">?</div>
        <div class="text-xs text-white/30 uppercase tracking-widest mt-2">Experience</div>
      </div>
    </div>

    <!-- PEEK STATE (Hover) -->
    <div 
      v-else-if="showMode === 'peek'"
      class="absolute inset-0 bg-white/5 backdrop-blur-sm border border-white/20 rounded-lg p-6 overflow-hidden"
    >
      <!-- Logo - Top Right -->
      <div class="absolute top-4 right-4 w-16 h-16 bg-white/10 rounded-lg flex items-center justify-center border border-white/20">
        <img 
          v-if="exp.logo" 
          :src="exp.logo" 
          :alt="`${exp.company} logo`"
          class="w-12 h-12 object-contain"
        />
        <span v-else class="text-2xl text-white/40">{{ exp.company.charAt(0) }}</span>
      </div>

      <!-- Peek content - just company and role -->
      <div class="space-y-3">
        <h3 class="text-2xl font-bold pr-20">{{ exp.company }}</h3>
        <p class="text-base text-gray-300">{{ exp.role }}</p>
        <p class="text-sm text-gray-500 font-mono">{{ exp.period }}</p>
      </div>

      <!-- Hint text -->
      <div class="absolute bottom-6 left-6 right-6 text-center">
        <div class="text-xs text-white/40 uppercase tracking-wider">
          Click to view details
        </div>
      </div>
    </div>

    <!-- FULL STATE (Active/Clicked) -->
    <div 
      v-else
      class="absolute inset-0 bg-white/5 backdrop-blur-sm border border-white/10 rounded-lg p-6 sm:p-8 overflow-y-auto hover:bg-white/[0.07] hover:border-white/20"
    >
      <!-- Logo - Top Right -->
      <div class="absolute top-4 right-4 w-16 h-16 bg-white/10 rounded-lg flex items-center justify-center border border-white/20">
        <img 
          v-if="exp.logo" 
          :src="exp.logo" 
          :alt="`${exp.company} logo`"
          class="w-12 h-12 object-contain"
        />
        <span v-else class="text-2xl text-white/40">{{ exp.company.charAt(0) }}</span>
      </div>

      <!-- Header -->
      <div class="mb-6 pb-6 border-b border-white/10 pr-20">
        <h3 class="text-2xl sm:text-3xl font-bold mb-2">{{ exp.company }}</h3>
        <p class="text-base sm:text-lg text-gray-300 mb-2">{{ exp.role }}</p>
        <p class="text-sm text-gray-500 font-mono">{{ exp.period }}</p>
      </div>

      <!-- Responsibilities -->
      <div class="mb-6 space-y-3">
        <div 
          v-for="(item, index) in exp.responsibilities" 
          :key="index" 
          class="flex items-start gap-3"
        >
          <span class="text-gray-500 mt-1 flex-shrink-0">—</span>
          <p class="text-sm sm:text-base text-gray-300 leading-relaxed">{{ item }}</p>
        </div>
      </div>

      <!-- Skills -->
      <div class="flex flex-wrap gap-2">
        <span
          v-for="skill in exp.skills"
          :key="skill"
          class="px-3 py-1 text-xs sm:text-sm bg-white/5 border border-white/10 rounded-full text-gray-400"
        >
          {{ skill }}
        </span>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  exp: {
    type: Object,
    required: true
  },
  isActive: {
    type: Boolean,
    default: false
  },
  isHovered: {
    type: Boolean,
    default: false
  },
  showMode: {
    type: String,
    default: 'blank', // 'blank' | 'peek' | 'full'
    validator: (value) => ['blank', 'peek', 'full'].includes(value)
  }
})
</script>

<style scoped>
/* Custom scrollbar for card content */
.overflow-y-auto::-webkit-scrollbar {
  width: 4px;
}
.overflow-y-auto::-webkit-scrollbar-track {
  background: rgba(255, 255, 255, 0.05);
  border-radius: 2px;
}
.overflow-y-auto::-webkit-scrollbar-thumb {
  background: rgba(255, 255, 255, 0.2);
  border-radius: 2px;
}
.overflow-y-auto::-webkit-scrollbar-thumb:hover {
  background: rgba(255, 255, 255, 0.3);
}
</style>
<template>
  <div class="mb-12 p-16">
    <div class="flex items-center gap-4 mb-4">
      <component :is="iconComponent" class="w-8 h-8" :class="iconColor" />
      <h2 class="text-4xl lg:text-5xl font-bold">{{ title }}</h2>
    </div>
    <p class="text-lg text-slate-400 max-w-3xl">
      {{ description }}
    </p>
    <div class="h-1 w-24 bg-gradient-to-r rounded-full mt-6" :class="gradient"></div>
  </div>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  title: {
    type: String,
    required: true
  },
  description: {
    type: String,
    required: true
  },
  icon: {
    type: String,
    default: 'briefcase'
  },
  gradient: {
    type: String,
    default: 'from-blue-500 to-purple-500'
  }
})

const iconComponent = computed(() => {
  if (props.icon === 'briefcase') {
    return {
      template: `
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 13.255A23.931 23.931 0 0112 15c-3.183 0-6.22-.62-9-1.745M16 6V4a2 2 0 00-2-2h-4a2 2 0 00-2 2v2m4 6h.01M5 20h14a2 2 0 002-2V8a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z" />
        </svg>
      `
    }
  } else if (props.icon === 'sparkles') {
    return {
      template: `
        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z" />
        </svg>
      `
    }
  }
  return { template: '<div></div>' }
})

const iconColor = computed(() => {
  return props.icon === 'briefcase' ? 'text-blue-400' : 'text-purple-400'
})
</script>
<template>
  <div class="min-h-screen bg-black text-white py-24 px-6">
    <div class="max-w-7xl mx-auto">
      <!-- Header -->
      <div class="mb-16">
        <h2 class="text-5xl md:text-6xl font-semibold tracking-tight mb-3">
          Available for work
        </h2>
        <p class="text-gray-500 text-lg">Open to new opportunities</p>
      </div>

      <!-- Desktop: Horizontal Grid -->
      <div class="hidden md:grid md:grid-cols-3 gap-px bg-gray-800">
        <div
          v-for="role in roles"
          :key="role.id"
          class="relative bg-black p-8 hover:bg-zinc-900 transition-colors duration-200 group"
        >
          <!-- Preferred Badge -->
          <div 
            v-if="role.preferred" 
            class="absolute -top-3 right-8 px-3 py-1 text-[10px] font-bold tracking-wider uppercase holographic overflow-hidden z-10 inline-block"
          >
            Preferred
          </div>

          <!-- Title & Level -->
          <div class="mb-6">
            <h3 class="text-2xl font-semibold mb-2">{{ role.title }}</h3>
            <span class="text-sm text-gray-500">{{ role.level }}</span>
          </div>

          <!-- Interest Bar -->
          <div class="mb-8">
            <div class="flex items-baseline justify-between mb-2">
              <span class="text-xs uppercase tracking-wider text-gray-600 font-medium">Interest</span>
              <span class="text-sm font-mono">{{ role.interest }}%</span>
            </div>
            <div class="h-1 bg-zinc-900 overflow-hidden">
              <div
                class="h-full bg-gradient-to-r from-yellow-400 via-yellow-500 to-amber-500 transition-all duration-700 ease-out"
                :style="{ width: `${role.interest}%` }"
              />
            </div>
          </div>

          <!-- Info Grid -->
          <div class="grid grid-cols-2 gap-6 text-sm">
            <!-- Location -->
            <div>
              <div class="text-xs uppercase tracking-wider text-gray-600 font-medium mb-2">
                Location
              </div>
              <div class="space-y-1.5">
                <div class="flex items-center gap-2">
                  <div :class="`w-1.5 h-1.5 rounded-full ${role.remote ? 'bg-white' : 'bg-gray-800'}`" />
                  <span :class="role.remote ? 'text-white' : 'text-gray-600'">Remote</span>
                </div>
                <div class="flex items-center gap-2">
                  <div :class="`w-1.5 h-1.5 rounded-full ${role.onsite ? 'bg-white' : 'bg-gray-800'}`" />
                  <span :class="role.onsite ? 'text-white' : 'text-gray-600'">On-site</span>
                </div>
              </div>
            </div>

            <!-- Employment -->
            <div>
              <div class="text-xs uppercase tracking-wider text-gray-600 font-medium mb-2">
                Type
              </div>
              <div class="flex flex-wrap gap-1.5">
                <span
                  v-for="(type, idx) in role.employment"
                  :key="idx"
                  class="px-2 py-0.5 text-xs border border-gray-800 text-gray-400"
                >
                  {{ type }}
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Mobile: Carousel -->
      <div class="md:hidden relative">
        <div 
          ref="carousel"
          class="flex overflow-x-auto snap-x snap-mandatory scrollbar-hide gap-4 pb-4"
          @scroll="updateActiveIndex"
        >
          <div
            v-for="role in roles"
            :key="role.id"
            class="flex-shrink-0 w-[85vw] snap-center relative bg-zinc-950 border border-gray-800 p-8"
          >
            <!-- Title & Level -->
            <div class="mb-6 flex items-center justify-between">
            <div>
                <h3 class="text-2xl font-semibold mb-2">{{ role.title }}</h3>
                <span class="text-sm text-gray-500">{{ role.level }}</span>
            </div>

            <div 
                v-if="role.preferred" 
                class="px-3 py-1 text-[10px] font-bold tracking-wider uppercase holographic overflow-hidden z-10 inline-block ml-4 self-start"
            >
                Preferred
            </div>
            </div>

            <!-- Interest Bar -->
            <div class="mb-8">
              <div class="flex items-baseline justify-between mb-2">
                <span class="text-xs uppercase tracking-wider text-gray-600 font-medium">Interest</span>
                <span class="text-sm font-mono">{{ role.interest }}%</span>
              </div>
              <div class="h-1 bg-zinc-900 overflow-hidden">
                <div
                  class="h-full bg-white transition-all duration-700 ease-out"
                  :style="{ width: `${role.interest}%` }"
                />
              </div>
            </div>

            <!-- Info Grid -->
            <div class="grid grid-cols-2 gap-6 text-sm">
              <!-- Location -->
              <div>
                <div class="text-xs uppercase tracking-wider text-gray-600 font-medium mb-2">
                  Location
                </div>
                <div class="space-y-1.5">
                  <div class="flex items-center gap-2">
                    <div :class="`w-1.5 h-1.5 rounded-full ${role.remote ? 'bg-white' : 'bg-gray-800'}`" />
                    <span :class="role.remote ? 'text-white' : 'text-gray-600'">Remote</span>
                  </div>
                  <div class="flex items-center gap-2">
                    <div :class="`w-1.5 h-1.5 rounded-full ${role.onsite ? 'bg-white' : 'bg-gray-800'}`" />
                    <span :class="role.onsite ? 'text-white' : 'text-gray-600'">On-site</span>
                  </div>
                </div>
              </div>

              <!-- Employment -->
              <div>
                <div class="text-xs uppercase tracking-wider text-gray-600 font-medium mb-2">
                  Type
                </div>
                <div class="flex flex-wrap gap-1.5">
                  <span
                    v-for="(type, idx) in role.employment"
                    :key="idx"
                    class="px-2 py-0.5 text-xs border border-gray-800 text-gray-400"
                  >
                    {{ type }}
                  </span>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Carousel Indicators -->
        <div class="flex justify-center gap-2 mt-6">
          <button
            v-for="(role, index) in roles"
            :key="role.id"
            @click="scrollToIndex(index)"
            :class="`h-1.5 rounded-full transition-all duration-300 ${
              activeIndex === index ? 'w-8 bg-white' : 'w-1.5 bg-gray-700'
            }`"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const roles = [
  {
    id: 1,
    title: "Web Developer",
    interest: 95,
    level: "Mid-level",
    remote: true,
    onsite: true,
    employment: ["Full-time", "Part-time"]
  },
  {
    id: 2,
    title: "Graphic Designer",
    interest: 88,
    level: "Junior",
    preferred: true,
    remote: true,
    onsite: true,
    employment: ["Full-time", "Part-time"]
  },
  {
    id: 3,
    title: "Video Editor",
    interest: 82,
    level: "Junior",
    remote: true,
    onsite: false,
    employment: ["Part-time"]
  }
]

const carousel = ref(null)
const activeIndex = ref(0)

const updateActiveIndex = () => {
  if (!carousel.value) return
  const scrollLeft = carousel.value.scrollLeft
  const cardWidth = carousel.value.offsetWidth * 0.85
  activeIndex.value = Math.round(scrollLeft / cardWidth)
}

const scrollToIndex = (index) => {
  if (!carousel.value) return
  const cardWidth = carousel.value.offsetWidth * 0.85
  carousel.value.scrollTo({
    left: cardWidth * index,
    behavior: 'smooth'
  })
}
</script>

<style scoped>
.scrollbar-hide::-webkit-scrollbar {
  display: none;
}
.scrollbar-hide {
  -ms-overflow-style: none;
  scrollbar-width: none;
}

.holographic {
  position: relative;
  background: linear-gradient(
    135deg,
    #fbbf24 0%,
    #f59e0b 25%,
    #fcd34d 50%,
    #f97316 75%,
    #fbbf24 100%
  );
  background-size: 200% 200%;
  animation: holographic-shift 3s ease infinite;
  color: #000000;
  font-weight: 900;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.3);
  box-shadow: 0 0 20px rgba(251, 191, 36, 0.5), inset 0 0 20px rgba(255, 255, 255, 0.3);
}

.holographic::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(255, 255, 255, 0.8),
    transparent
  );
  animation: holographic-shine 2s infinite;
}

@keyframes holographic-shift {
  0%, 100% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
}

@keyframes holographic-shine {
  0% {
    left: -100%;
  }
  50%, 100% {
    left: 200%;
  }
}
</style>
<template>
  <section class="w-full bg-black text-white py-12 sm:py-16 lg:py-24 xl:py-32 overflow-hidden">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      
      <!-- MOBILE LAYOUT (< lg) -->
      <div class="lg:hidden space-y-8">
        <!-- Title & Stats -->
        <div class="space-y-6">
          <h2 class="text-5xl sm:text-6xl md:text-7xl font-bold leading-none">
            WORK<br />EXPERIENCE
          </h2>
          
          <!-- Stats - Side by side -->
          <div class="flex items-center gap-8 sm:gap-12 border-l border-white/10 pl-6">
            <div>
              <div class="text-4xl sm:text-5xl font-bold font-mono">{{ totalYears }}+</div>
              <div class="text-xs sm:text-sm text-gray-400 uppercase tracking-wider mt-1">Years</div>
            </div>
            <div class="w-px h-12 bg-white/10"></div>
            <div>
              <div class="text-4xl sm:text-5xl font-bold font-mono">{{ totalRoles }}</div>
              <div class="text-xs sm:text-sm text-gray-400 uppercase tracking-wider mt-1">Roles</div>
            </div>
          </div>
          
          <p class="text-sm text-gray-500 uppercase tracking-wider">
            Swipe to explore →
          </p>
        </div>

        <!-- Cards Carousel -->
        <div class="w-full">
          <div class="overflow-x-auto scrollbar-hide -mx-4 px-4 pb-2">
            <div class="flex gap-4 snap-x snap-mandatory">
              <div 
                v-for="(exp, index) in experiences" 
                :key="exp.id" 
                @click="activeCard = index"
                class="flex-shrink-0 w-[280px] xs:w-[320px] sm:w-[360px] snap-center"
              >
                <ExperienceCard 
                  :exp="exp" 
                  :is-active="true" 
                  :is-hovered="false" 
                  show-mode="full" 
                />
              </div>
            </div>
          </div>
          
          <!-- Scroll indicator -->
          <div class="flex justify-center gap-2 mt-6">
            <div
              v-for="(_, index) in experiences"
              :key="index"
              :class="[
                'h-1.5 rounded-full transition-all duration-300',
                index === activeCard ? 'w-10 bg-white' : 'w-1.5 bg-white/30'
              ]"
            />
          </div>
        </div>
      </div>

      <!-- DESKTOP LAYOUT (>= lg) -->
      <div class="hidden lg:flex gap-16 xl:gap-20">
        
        <!-- LEFT SIDE - Title & Stats -->
        <div class="lg:w-1/3 space-y-8">
          <div>
            <h2 class="text-5xl xl:text-7xl font-bold mb-12 leading-none">
              WORK<br />EXPERIENCE
            </h2>
            
            <!-- Stats -->
            <div class="space-y-6 border-l border-white/10 pl-6">
              <div>
                <div class="text-6xl font-bold font-mono">{{ totalYears }}+</div>
                <div class="text-sm text-gray-400 uppercase tracking-wider mt-1">Years</div>
              </div>
              <div>
                <div class="text-6xl font-bold font-mono">{{ totalRoles }}</div>
                <div class="text-sm text-gray-400 uppercase tracking-wider mt-1">Roles</div>
              </div>
            </div>
          </div>

          <!-- Desktop navigation hint -->
          <div class="text-xs text-gray-500 uppercase tracking-wider">
            Hover to peek • Click to expand →
          </div>
        </div>

        <!-- RIGHT SIDE - Card Stack -->
        <div class="lg:w-2/3">
          <div 
            class="relative w-full overflow-visible"
            :style="{ 
              height: '550px',
              minHeight: '550px'
            }"
          >
            <!-- Cards container with calculated width -->
            <div 
              class="relative w-full h-full"
              :style="{ 
                paddingRight: `${calculateContainerPadding()}px`
              }"
            >
              <div
                v-for="(exp, index) in experiences"
                :key="exp.id"
                @mouseenter="hoveredCard = index"
                @mouseleave="hoveredCard = null"
                @click="handleCardClick(index)"
                class="absolute top-0 cursor-pointer transition-all duration-500 ease-out"
                :style="getCardStyle(index)"
              >
                <ExperienceCard 
                  :exp="exp" 
                  :is-active="activeCard === index"
                  :is-hovered="hoveredCard === index"
                  :show-mode="getShowMode(index)"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const activeCard = ref(0) // Kopii card active by default
const hoveredCard = ref(null)

const experiences = [
  {
    id: 0,
    company: 'Kopii Computer',
    logo: '/kopii-logo.png',
    role: 'Assistant Technician & Aftersale Service',
    period: '2020 - 2022',
    responsibilities: [
      'Managed PC assembly and troubleshooting',
      'Handled customer inquiries and repairs',
      'Provided after-sales support'
    ],
    skills: ['Hardware', 'Customer Service', 'Troubleshooting']
  },
  {
    id: 1,
    company: 'Ssquad Global',
    logo: '/ssquad-logo.png',
    role: 'Service Desk Analyst',
    period: '2023',
    responsibilities: [
      'Provided Level 1 IT support',
      'Troubleshot software and hardware issues',
      'Assisted with sales reconciliation'
    ],
    skills: ['IT Support', 'Troubleshooting', 'Client Service']
  },
  {
    id: 2,
    company: 'CTRLPC',
    logo: '/ctrlpclogo.png',
    role: 'Technician, Web Dev & Video Editor',
    period: '2023 - 2024',
    responsibilities: [
      'Built company landing page with Vue.js & TailwindCSS',
      'Produced TikTok content for service promotion',
      'Managed PC assembly and customer support'
    ],
    skills: ['Vue.js', 'TailwindCSS', 'Video Editing', 'Hardware']
  },
  {
    id: 3,
    company: 'Self-Work',
    logo: '/self-work-logo.png',
    role: 'Full-Stack Web Developer',
    period: '2024 - Present',
    responsibilities: [
      'Built web application using Django & Vue.js',
      'Developed AI-driven workflow automation',
      'Integrated APIs and external services'
    ],
    skills: ['Django', 'Vue.js', 'PostgreSQL', 'n8n', 'AI']
  },
  {
    id: 4,
    company: 'Dareia Coffee',
    logo: '/dclogo.png',
    role: 'Graphic Designer',
    period: '2023 - Present',
    responsibilities: [
      'Designed visual identity and brand materials',
      'Created menu boards, banners, and social graphics',
      'Produced promotional videos for online presence'
    ],
    skills: ['Photoshop', 'Brand Identity', 'Video Production']
  }
]

const totalYears = computed(() => 4)
const totalRoles = computed(() => experiences.length)

// Calculate container padding to prevent cutoff
const calculateContainerPadding = () => {
  const cardWidth = 340
  const stackedWidth = 80
  const totalCards = experiences.length
  
  // Total width needed: stacked cards + one full expanded card
  const totalWidth = (activeCard.value * stackedWidth) + cardWidth + ((totalCards - activeCard.value - 1) * stackedWidth)
  
  // Add extra padding for hover effect
  return Math.max(0, totalWidth - 600) + 50 // 50px extra buffer
}

const handleCardClick = (index) => {
  activeCard.value = index
}

const getShowMode = (index) => {
  if (activeCard.value === index) return 'full'
  if (hoveredCard.value === index) return 'peek'
  return 'blank'
}

const getCardStyle = (index) => {
  const isActive = activeCard.value === index
  const isHovered = hoveredCard.value === index
  const totalCards = experiences.length
  
  // Base dimensions
  const cardWidth = 340
  const stackedWidth = 80
  
  // Calculate horizontal position
  let left = 0
  
  if (isActive) {
    left = index * stackedWidth
  } else if (index < activeCard.value) {
    left = index * stackedWidth
  } else {
    left = (activeCard.value * stackedWidth) + cardWidth + ((index - activeCard.value - 1) * stackedWidth)
  }
  
  // Hover effect: pull out slightly
  if (isHovered && !isActive) {
    left += 15
  }
  
  // Z-index management
  let zIndex = totalCards - Math.abs(index - activeCard.value)
  if (isHovered && !isActive) zIndex = totalCards + 1
  if (isActive) zIndex = totalCards + 2
  
  // Scale and vertical movement
  const scale = isActive ? 1 : (isHovered ? 0.98 : 0.95)
  const translateY = isActive ? -10 : (isHovered ? -5 : 0)
  
  return {
    left: `${left}px`,
    transform: `translateY(${translateY}px) scale(${scale})`,
    zIndex,
    width: `${cardWidth}px`,
    height: '500px',
    transition: 'all 0.5s cubic-bezier(0.4, 0, 0.2, 1)'
  }
}
</script>

<style scoped>
/* Hide scrollbar for mobile carousel */
.scrollbar-hide::-webkit-scrollbar {
  display: none;
}
.scrollbar-hide {
  -ms-overflow-style: none;
  scrollbar-width: none;
}

/* Ensure no overflow issues */
@media (min-width: 1024px) {
  .lg\:w-2\/3 {
    min-width: 0; /* Prevent flex item from overflowing */
  }
}
</style>
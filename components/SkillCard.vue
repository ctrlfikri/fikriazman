<template>
  <section class="relative py-8 sm:py-12 md:py-16 lg:py-20 bg-black text-white overflow-hidden  flex items-center">
    <!-- Background Orbs - Responsive positioning -->
    <div class="absolute top-0 left-[10%] sm:left-[15%] md:left-[20%] lg:left-1/4 w-[15rem] h-[15rem] sm:w-[20rem] sm:h-[20rem] md:w-[25rem] md:h-[25rem] lg:w-[30rem] lg:h-[30rem] bg-purple-500/20 rounded-full blur-[80px] sm:blur-[100px] md:blur-[120px] animate-pulse-slow"></div>
    <div class="absolute bottom-0 right-[10%] sm:right-[15%] md:right-[20%] lg:right-1/4 w-[15rem] h-[15rem] sm:w-[20rem] sm:h-[20rem] md:w-[25rem] md:h-[25rem] lg:w-[30rem] lg:h-[30rem] bg-blue-500/20 rounded-full blur-[80px] sm:blur-[100px] md:blur-[120px]" style="animation-delay:1s;"></div>

    <div class="relative z-10 w-full max-w-7xl mx-auto px-3 sm:px-4 md:px-6 lg:px-8">
      <div class="flex flex-col items-center gap-6 sm:gap-8 md:gap-10 lg:gap-12">
        
        <!-- Tabs - Fully responsive -->
        <div class="w-full max-w-full sm:max-w-md md:max-w-lg lg:max-w-xl px-2">
          <div class="relative flex bg-white/10 rounded-full p-1 w-full backdrop-blur-sm">
            <!-- Active tab indicator -->
            <div 
              class="absolute top-1 bottom-1 bg-white rounded-full transition-all duration-300 ease-out"
              :style="{
                left: `${(currentTabIndex / tabs.length) * 100}%`,
                width: `${100 / tabs.length}%`,
                transform: 'translateX(0.25rem)',
                right: 'auto',
                marginRight: '0.25rem'
              }"
            ></div>

            <button
              v-for="tab in tabs"
              :key="tab.id"
              @click="switchTab(tab.id)"
              class="relative flex-1 py-2 sm:py-2.5 md:py-3 px-2 text-xs sm:text-sm md:text-base font-semibold z-10 transition-colors rounded-full"
              :class="currentTab === tab.id ? 'text-black' : 'text-white/70 hover:text-white'"
            >
              <span class="block truncate">{{ tab.title }}</span>
            </button>
          </div>
        </div>

        <!-- Card Carousel Container - Responsive height and spacing -->
        <div class="relative w-full flex justify-center items-center px-2 sm:px-4 md:px-8">
          <div class="relative flex justify-center items-center w-full min-h-[420px] sm:min-h-[450px] md:min-h-[500px] lg:min-h-[520px]">
            
            <!-- Background Animated Lights - Responsive -->
            <div class="absolute inset-0 -z-10 pointer-events-none overflow-hidden rounded-3xl opacity-60 sm:opacity-70 md:opacity-80">
              <div
                class="absolute w-40 h-40 sm:w-52 sm:h-52 md:w-64 md:h-64 lg:w-72 lg:h-72 rounded-full bg-yellow-400/30 blur-2xl sm:blur-3xl animate-light-move"
                style="top:10%; left:20%;"
              ></div>
              <div
                class="absolute w-36 h-36 sm:w-48 sm:h-48 md:w-56 md:h-56 lg:w-60 lg:h-60 rounded-full bg-orange-400/30 blur-2xl sm:blur-3xl animate-light-move"
                style="top:50%; left:60%; animation-delay:2s;"
              ></div>
              <div
                class="absolute w-48 h-48 sm:w-60 sm:h-60 md:w-72 md:h-72 lg:w-80 lg:h-80 rounded-full bg-red-400/20 blur-2xl sm:blur-3xl animate-light-move"
                style="top:70%; left:30%; animation-delay:4s;"
              ></div>
            </div>

            <!-- Navigation Buttons Container -->
            <div class="absolute inset-x-0 top-1/2 -translate-y-1/2 flex justify-between items-center px-0 sm:px-2 md:px-4 pointer-events-none z-30">
              <!-- Prev Button - Responsive -->
              <button
                class="pointer-events-auto text-xl sm:text-2xl md:text-3xl p-2 sm:p-2.5 md:p-3 rounded-full bg-white/10 hover:bg-white/20 active:bg-white/30 transition-all backdrop-blur-sm border border-white/10 shadow-lg hover:scale-110 active:scale-95"
                @click="prevCard"
                aria-label="Previous skill"
              >
                ‹
              </button>

              <!-- Next Button - Responsive -->
              <button
                class="pointer-events-auto text-xl sm:text-2xl md:text-3xl p-2 sm:p-2.5 md:p-3 rounded-full bg-white/10 hover:bg-white/20 active:bg-white/30 transition-all backdrop-blur-sm border border-white/10 shadow-lg hover:scale-110 active:scale-95"
                @click="nextCard"
                aria-label="Next skill"
              >
                ›
              </button>
            </div>

            <!-- Skill Card - Fully responsive -->
            <transition :name="transitionName" mode="out-in">
              <div
                v-if="currentSkill"
                :key="currentSkill.name + currentTab"
                ref="card"
                class="w-full max-w-[280px] xs:max-w-[320px] sm:max-w-[360px] md:max-w-[400px] lg:max-w-[450px] mx-auto p-4 sm:p-5 md:p-6 bg-white/5 backdrop-blur-xl rounded-2xl sm:rounded-3xl border border-white/10 shadow-2xl overflow-hidden cursor-pointer transition-shadow duration-300"
                @mousemove="updateTilt"
                @mouseleave="resetTilt"
                @touchstart="resetTilt"
                :style="[cardStyle, shadowStyle]"
              >
                <!-- Expert Badge - Responsive -->
                <div
                  v-if="currentSkill.expert"
                  class="absolute top-3 right-3 sm:top-4 sm:right-4 z-20 px-2 py-1 sm:px-3 sm:py-1.5 rounded-full bg-gradient-to-r from-yellow-400 to-orange-500 font-black text-black shadow-lg border border-yellow-300 text-[10px] sm:text-xs animate-bounce-slow"
                >
                  ⚡ EXPERT
                </div>

                <!-- Icon & Name - Responsive -->
                <div class="flex items-start gap-3 sm:gap-4 mb-4 sm:mb-5 md:mb-6">
                  <div
                    class="w-12 h-12 sm:w-14 sm:h-14 md:w-16 md:h-16 rounded-xl sm:rounded-2xl bg-gradient-to-br from-white/20 to-white/5 flex items-center justify-center text-2xl sm:text-3xl md:text-4xl border border-white/20 animate-pulse-icon flex-shrink-0"
                  >
                    {{ currentSkill.icon }}
                  </div>
                  <div class="flex-1 min-w-0 pt-1">
                    <h3 class="text-base sm:text-lg md:text-xl lg:text-2xl font-bold truncate">{{ currentSkill.name }}</h3>
                    <p class="text-xs sm:text-sm text-white/50 truncate">{{ currentSkill.category }}</p>
                  </div>
                </div>

                <!-- Proficiency - Responsive -->
                <div class="space-y-2 sm:space-y-3 mb-4 sm:mb-5">
                  <div class="flex justify-between items-center text-xs sm:text-sm">
                    <span class="text-white/70 font-medium">Proficiency</span>
                    <span class="text-base sm:text-lg md:text-xl font-bold tabular-nums">{{ animatedLevel }}%</span>
                  </div>
                  <div class="relative h-1.5 sm:h-2 bg-white/10 rounded-full overflow-hidden">
                    <div
                      class="absolute inset-y-0 left-0 rounded-full transition-all duration-700 ease-out"
                      :style="{ 
                        width: animatedLevel + '%', 
                        background: currentSkill.expert 
                          ? 'linear-gradient(90deg,#fbbf24,#f97316,#fbbf24)' 
                          : 'linear-gradient(90deg,#8b5cf6,#ec4899,#3b82f6)'
                      }"
                    ></div>
                  </div>
                </div>

                <!-- Tags - Responsive with proper wrapping -->
                <div class="flex flex-wrap gap-1.5 sm:gap-2 justify-center sm:justify-start">
                  <transition-group name="tag-fade">
                    <span
                      v-for="tag in currentSkill.tags"
                      :key="tag"
                      class="px-2 py-0.5 sm:px-3 sm:py-1 text-[10px] sm:text-xs md:text-sm rounded-full bg-white/5 text-white/60 border border-white/10 whitespace-nowrap"
                    >
                      {{ tag }}
                    </span>
                  </transition-group>
                </div>

                <!-- Card Counter - Responsive -->
                <div class="mt-4 sm:mt-5 pt-3 sm:pt-4 border-t border-white/10 text-center">
                  <span class="text-[10px] sm:text-xs text-white/40">
                    {{ currentIndex + 1 }} / {{ filteredSkills.length }}
                  </span>
                </div>
              </div>
            </transition>
          </div>
        </div>

        <!-- Optional: Keyboard hint for desktop -->
        <div class="hidden md:block text-center text-xs text-white/30 mt-2">
          Use ← → arrow keys to navigate
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, watch, onMounted, onUnmounted } from 'vue'

const tabs = [
  { id: 'web', title: 'Web' },
  { id: 'graphic', title: 'Graphic' },
  { id: 'video', title: 'Video' },
  { id: 'technical', title: 'Technical' },
]

const currentTab = ref('web')
const currentIndex = ref(0)
const animatedLevel = ref(0)
const transitionName = ref('card-swipe')
const transitionDirection = ref('next')

const skills = [
  { tab: 'web', name: 'Nuxt.js', level: 90, expert: true, icon: '⚡', category: 'Frontend', tags: ['Nuxt 3','Composition API','Pinia'] },
  { tab: 'web', name: 'TailwindCSS', level: 85, expert: true, icon: '🎨', category: 'CSS', tags: ['Responsive','Utility-first'] },
  { tab: 'web', name: 'Django', level: 80, expert: true, icon: '🐍', category: 'Backend', tags: ['ORM','Auth','REST API'] },
  { tab: 'web', name: 'PostgreSQL', level: 75, expert: true, icon: '🐘', category: 'Database', tags: ['SQL','Queries'] },
  { tab: 'graphic', name: 'Photoshop', level: 90, expert: true, icon: '🖼️', category: 'Photo', tags: ['Retouching','Digital Art'] },
  { tab: 'graphic', name: 'Illustrator', level: 70, expert: false, icon: '✏️', category: 'Vector', tags: ['Logos','Icons'] },
  { tab: 'video', name: 'CapCut', level: 90, expert: true, icon: '✂️', category: 'Mobile Editor', tags: ['Quick Edits','Reels'] },
  { tab: 'video', name: 'Vegas Pro', level: 85, expert: true, icon: '🎞️', category: 'Video Editor', tags: ['Timeline','Effects','Pro'] },
  { tab: 'technical', name: 'Hardware', level: 85, expert: true, icon: '🔩', category: 'PC Build', tags: ['Assembly','Troubleshoot'] },
  { tab: 'technical', name: 'BSOD Analysis', level: 75, expert: false, icon: '🔍', category: 'Troubleshoot', tags: ['Crash Dumps','Windows'] },
]

const filteredSkills = computed(() => skills.filter(s => s.tab === currentTab.value))
const currentSkill = computed(() => filteredSkills.value[currentIndex.value])
const currentTabIndex = computed(() => tabs.findIndex(tab => tab.id === currentTab.value))

// Tilt physics (disabled on mobile)
const card = ref(null)
const tilt = ref({ x:0, y:0 })
const targetTilt = ref({ x:0, y:0 })
const isMobile = ref(false)

function lerp(a,b,n){ return (1-n)*a + n*b }

function updateTilt(e){
  if (isMobile.value) return
  if (!card.value) return
  
  const rect = card.value.getBoundingClientRect()
  const cx = rect.width/2
  const cy = rect.height/2
  const dx = e.clientX - rect.left - cx
  const dy = e.clientY - rect.top - cy
  targetTilt.value.x = (dy/cy)*-10
  targetTilt.value.y = (dx/cx)*10
}

function resetTilt(){ 
  targetTilt.value.x = 0
  targetTilt.value.y = 0 
}

let animationFrameId = null

onMounted(()=>{ 
  // Check if mobile
  isMobile.value = window.innerWidth < 768
  
  const handleResize = () => {
    isMobile.value = window.innerWidth < 768
    if (isMobile.value) resetTilt()
  }
  window.addEventListener('resize', handleResize)
  
  // Tilt animation loop
  function animate(){
    tilt.value.x = lerp(tilt.value.x, targetTilt.value.x, 0.15)
    tilt.value.y = lerp(tilt.value.y, targetTilt.value.y, 0.15)
    animationFrameId = requestAnimationFrame(animate)
  }
  animate()

  // Keyboard navigation
  const handleKeydown = (e) => {
    if (e.key === 'ArrowLeft') prevCard()
    if (e.key === 'ArrowRight') nextCard()
  }
  window.addEventListener('keydown', handleKeydown)

  onUnmounted(() => {
    if (animationFrameId) cancelAnimationFrame(animationFrameId)
    window.removeEventListener('resize', handleResize)
    window.removeEventListener('keydown', handleKeydown)
  })
})

// Card styles
const cardStyle = computed(() => {
  if (isMobile.value) {
    return { transform: 'none' }
  }
  return {
    transform: `perspective(1000px) rotateX(${tilt.value.x}deg) rotateY(${tilt.value.y}deg) scale3d(1.02,1.02,1.02)`,
    transition: 'transform 0.05s'
  }
})

const shadowStyle = computed(() => {
  if (isMobile.value) {
    return { boxShadow: '0 20px 60px rgba(255,255,255,0.1)' }
  }
  return {
    boxShadow: `${tilt.value.y*2}px ${tilt.value.x*2}px 60px rgba(255,255,255,0.15)`
  }
})

// Animate Proficiency
watch(currentSkill, skill=>{
  if (!skill) return
  animatedLevel.value = 0
  
  // Only run animation on client side
  if (typeof window === 'undefined') {
    animatedLevel.value = skill.level
    return
  }
  
  let start = 0
  const duration = 700
  const step = 16
  const increment = skill.level / (duration/step)
  let rafId = null
  
  function anim(){
    start += increment
    if(start < skill.level){
      animatedLevel.value = Math.floor(start)
      rafId = requestAnimationFrame(anim)
    } else {
      animatedLevel.value = skill.level
    }
  }
  anim()
  
  // Cleanup function
  return () => {
    if (rafId) cancelAnimationFrame(rafId)
  }
}, { immediate: true })

// Navigation
function nextCard(){ 
  transitionName.value = 'slide-left'
  transitionDirection.value = 'next'
  currentIndex.value = (currentIndex.value+1) % filteredSkills.value.length 
}

function prevCard(){ 
  transitionName.value = 'slide-right'
  transitionDirection.value = 'prev'
  currentIndex.value = (currentIndex.value-1+filteredSkills.value.length) % filteredSkills.value.length 
}

function switchTab(tabId){ 
  transitionName.value = 'card-flip'
  currentTab.value = tabId
  currentIndex.value = 0 
}
</script>

<style scoped>
/* ========== SLIDE LEFT TRANSITION (Next) ========== */
.slide-left-enter-active {
  animation: slideInFromRight 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}
.slide-left-leave-active {
  animation: slideOutToLeft 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

@keyframes slideInFromRight {
  0% {
    transform: translateX(120%) rotateY(90deg) scale(0.8);
    opacity: 0;
  }
  60% {
    transform: translateX(-5%) rotateY(-5deg) scale(1.05);
    opacity: 1;
  }
  100% {
    transform: translateX(0) rotateY(0deg) scale(1);
    opacity: 1;
  }
}

@keyframes slideOutToLeft {
  0% {
    transform: translateX(0) rotateY(0deg) scale(1);
    opacity: 1;
  }
  100% {
    transform: translateX(-120%) rotateY(-90deg) scale(0.8);
    opacity: 0;
  }
}

/* ========== SLIDE RIGHT TRANSITION (Previous) ========== */
.slide-right-enter-active {
  animation: slideInFromLeft 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}
.slide-right-leave-active {
  animation: slideOutToRight 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

@keyframes slideInFromLeft {
  0% {
    transform: translateX(-120%) rotateY(-90deg) scale(0.8);
    opacity: 0;
  }
  60% {
    transform: translateX(5%) rotateY(5deg) scale(1.05);
    opacity: 1;
  }
  100% {
    transform: translateX(0) rotateY(0deg) scale(1);
    opacity: 1;
  }
}

@keyframes slideOutToRight {
  0% {
    transform: translateX(0) rotateY(0deg) scale(1);
    opacity: 1;
  }
  100% {
    transform: translateX(120%) rotateY(90deg) scale(0.8);
    opacity: 0;
  }
}

/* ========== FLIP TRANSITION (Tab Change) ========== */
.card-flip-enter-active {
  animation: flipIn 0.8s cubic-bezier(0.25, 0.46, 0.45, 0.94);
}
.card-flip-leave-active {
  animation: flipOut 0.6s cubic-bezier(0.55, 0.085, 0.68, 0.53);
}

@keyframes flipIn {
  0% {
    transform: perspective(1000px) rotateX(-90deg) translateY(50px) scale(0.8);
    opacity: 0;
    filter: blur(10px);
  }
  50% {
    transform: perspective(1000px) rotateX(10deg) translateY(-10px) scale(1.05);
    opacity: 0.8;
    filter: blur(2px);
  }
  100% {
    transform: perspective(1000px) rotateX(0deg) translateY(0) scale(1);
    opacity: 1;
    filter: blur(0);
  }
}

@keyframes flipOut {
  0% {
    transform: perspective(1000px) rotateX(0deg) translateY(0) scale(1);
    opacity: 1;
    filter: blur(0);
  }
  100% {
    transform: perspective(1000px) rotateX(90deg) translateY(-50px) scale(0.8);
    opacity: 0;
    filter: blur(10px);
  }
}

/* Old card-swipe fallback */
.card-swipe-enter-active { 
  animation: card-enter 0.6s cubic-bezier(.65,.05,.36,1); 
}
.card-swipe-leave-active { 
  animation: card-leave 0.5s cubic-bezier(.65,.05,.36,1); 
}

@keyframes card-enter { 
  0% { transform: translateY(40px) scale(0.9); opacity:0; } 
  60% { transform: translateY(-10px) scale(1.05); opacity:1; } 
  100% { transform: translateY(0px) scale(1); opacity:1; } 
}

@keyframes card-leave { 
  0% { transform: translateY(0) scale(1); opacity:1; } 
  100% { transform: translateY(-30px) scale(0.9); opacity:0; } 
}

/* Tag fade animation */
.tag-fade-enter-active { 
  transition: all 0.5s ease-out; 
}
.tag-fade-enter-from { 
  opacity:0; 
  transform: translateY(10px); 
}
.tag-fade-enter-to { 
  opacity:1; 
  transform: translateY(0); 
}

/* Background pulse */
.animate-pulse-slow { 
  animation: pulse-slow 6s ease-in-out infinite; 
}

@keyframes pulse-slow { 
  0%,100% {opacity:0.3; transform:scale(1);} 
  50% {opacity:0.5; transform:scale(1.1);} 
}

/* Icon pulse */
@keyframes pulse-icon { 
  0%,100% { transform: scale(1); } 
  50% { transform: scale(1.08); } 
}
.animate-pulse-icon { 
  animation: pulse-icon 2s ease-in-out infinite; 
}

/* Expert badge bounce */
@keyframes bounce-slow { 
  0%,100% {transform: translateY(0);} 
  50% {transform: translateY(-5px);} 
}
.animate-bounce-slow { 
  animation: bounce-slow 2s ease-in-out infinite; 
}

/* Ambient moving lights */
@keyframes light-move {
  0% { transform: translate(0,0) scale(1); opacity:0.3; }
  50% { transform: translate(20px, -30px) scale(1.1); opacity:0.5; }
  100% { transform: translate(0,0) scale(1); opacity:0.3; }
}
.animate-light-move { 
  animation: light-move 8s ease-in-out infinite; 
}

/* Smooth transitions for all interactive elements */
button {
  -webkit-tap-highlight-color: transparent;
}
</style>
<template>
  <section class="relative py-16 bg-black text-white overflow-hidden">
    <!-- Background Orbs -->
    <div class="absolute top-0 left-1/4 w-[30rem] h-[30rem] bg-purple-500/20 rounded-full blur-[120px] animate-pulse-slow"></div>
    <div class="absolute bottom-0 right-1/4 w-[30rem] h-[30rem] bg-blue-500/20 rounded-full blur-[120px]" style="animation-delay:1s;"></div>

    <div class="relative z-10 max-w-7xl mx-auto px-4 flex flex-col items-center gap-12">
      <!-- Tabs -->
      <div class="relative flex bg-white/10 rounded-full p-1 w-full max-w-md justify-center">

        <button
          v-for="tab in tabs"
          :key="tab.id"
          @click="switchTab(tab.id)"
          class="relative flex-1 py-2 text-sm font-semibold z-10 text-white transition-colors"
          :class="currentTab === tab.id ? 'text-black' : 'text-white/70 hover:text-white'"
        >
          {{ tab.title }}
        </button>
      </div>

      <!-- Card Carousel -->
      <div class="relative flex justify-center items-center h-[500px] w-full">
        <!-- Background Animated Lights -->
        <div class="absolute inset-0 -z-10 pointer-events-none overflow-hidden rounded-3xl">
          <div
            class="absolute w-72 h-72 rounded-full bg-yellow-400/30 blur-3xl animate-light-move"
            style="top:10%; left:20%;"
          ></div>
          <div
            class="absolute w-60 h-60 rounded-full bg-orange-400/30 blur-3xl animate-light-move"
            style="top:50%; left:60%; animation-delay:2s;"
          ></div>
          <div
            class="absolute w-80 h-80 rounded-full bg-red-400/20 blur-3xl animate-light-move"
            style="top:70%; left:30%; animation-delay:4s;"
          ></div>
        </div>

        <!-- Prev Button -->
        <button
          class="absolute left-0 text-3xl p-3 rounded-full bg-white/10 hover:bg-white/20 transition-colors z-20"
          @click="prevCard"
        >
          ‹
        </button>

        <!-- Skill Card -->
        <transition name="card-swipe" mode="out-in">
          <div
            v-if="currentSkill"
            :key="currentSkill.name + currentTab"
            ref="card"
            class="absolute w-[360px] sm:w-[400px] md:w-[450px] p-6 bg-white/5 backdrop-blur-xl rounded-3xl border border-white/10 shadow-lg overflow-hidden cursor-pointer"
            @mousemove="updateTilt"
            @mouseleave="resetTilt"
            :style="[cardStyle, shadowStyle]"
          >
            <!-- Expert Badge -->
            <div
              v-if="currentSkill.expert"
              class="absolute top-4 right-4 z-20 px-3 py-1 rounded-full bg-gradient-to-r from-yellow-400 to-orange-500 font-black text-black shadow-lg border border-yellow-300 text-xs animate-bounce-slow"
            >
              ⚡ EXPERT
            </div>

            <!-- Icon & Name -->
            <div class="flex items-start gap-4 mb-6">
              <div
                class="w-14 h-14 rounded-2xl bg-gradient-to-br from-white/20 to-white/5 flex items-center justify-center text-3xl border border-white/20 animate-pulse-icon"
              >
                {{ currentSkill.icon }}
              </div>
              <div class="flex-1">
                <h3 class="text-xl font-bold">{{ currentSkill.name }}</h3>
                <p class="text-sm text-white/50">{{ currentSkill.category }}</p>
              </div>
            </div>

            <!-- Proficiency -->
            <div class="space-y-3">
              <div class="flex justify-between items-center text-sm">
                <span class="text-white/70 font-medium">Proficiency</span>
                <span class="text-lg font-bold">{{ animatedLevel }}%</span>
              </div>
              <div class="relative h-2 bg-white/10 rounded-full overflow-hidden">
                <div
                  class="absolute inset-0 rounded-full transition-all duration-700 ease-out"
                  :style="{ width: animatedLevel + '%', background: currentSkill.expert ? 'linear-gradient(90deg,#fbbf24,#f97316,#fbbf24)' : 'linear-gradient(90deg,#8b5cf6,#ec4899,#3b82f6)'}"
                ></div>
              </div>
            </div>

            <!-- Tags -->
            <div class="flex flex-wrap gap-2 mt-4 justify-center sm:justify-start">
              <transition-group name="tag-fade" tag="div">
                <span
                  v-for="tag in currentSkill.tags"
                  :key="tag"
                  class="px-3 py-1 text-xs sm:text-sm rounded-full bg-white/5 text-white/60 border border-white/10"
                >
                  {{ tag }}
                </span>
              </transition-group>
            </div>
          </div>
        </transition>

        <!-- Next Button -->
        <button
          class="absolute right-0 text-3xl p-3 rounded-full bg-white/10 hover:bg-white/20 transition-colors z-20"
          @click="nextCard"
        >
          ›
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, watch, onMounted } from 'vue'

const tabs = [
  { id: 'web', title: 'Web' },
  { id: 'graphic', title: 'Graphic' },
  { id: 'video', title: 'Video Editing' },
  { id: 'technical', title: 'Technical' },
]

const currentTab = ref('web')
const currentIndex = ref(0)
const animatedLevel = ref(0)

const skills = [
  { tab: 'web', name: 'Vue.js', level: 90, expert: true, icon: '⚡', category: 'Frontend', tags: ['Nuxt 3','Composition API','Pinia'] },
  { tab: 'web', name: 'TailwindCSS', level: 85, expert: true, icon: '🎨', category: 'CSS', tags: ['Responsive','Utility-first'] },
  { tab: 'web', name: 'Django', level: 80, expert: true, icon: '🐍', category: 'Backend', tags: ['ORM','Auth','REST API'] },
  { tab: 'web', name: 'PostgreSQL', level: 75, expert: true, icon: '🐘', category: 'Database', tags: ['SQL','Queries'] },
  { tab: 'graphic', name: 'Photoshop', level: 90, expert: true, icon: '🖼️', category: 'Photo', tags: ['Retouching','Digital Art'] },
  { tab: 'graphic', name: 'Illustrator', level: 70, expert: false, icon: '✏️', category: 'Vector', tags: ['Logos','Icons'] },
  { tab: 'video', name: 'CapCut', level: 90, expert: true, icon: '✂️', category: 'Mobile Editor', tags: ['Quick Edits','Reels'] },
  { tab: 'video', name: 'Vegas Pro', level: 85, expert: true, icon: '🎞️', category: 'Video Editor', tags: ['Timeline','Effects','Professional'] },
  { tab: 'technical', name: 'Hardware', level: 85, expert: true, icon: '🔩', category: 'PC Build', tags: ['Assembly','Troubleshoot'] },
  { tab: 'technical', name: 'BSOD Analysis', level: 75, expert: false, icon: '🔍', category: 'Troubleshoot', tags: ['Crash Dumps','Windows'] },
]

const filteredSkills = computed(() => skills.filter(s => s.tab === currentTab.value))
const currentSkill = computed(() => filteredSkills.value[currentIndex.value])
const currentTabIndex = computed(() => tabs.findIndex(tab => tab.id === currentTab.value))

// Tilt physics
const card = ref(null)
const tilt = ref({ x:0, y:0 })
const targetTilt = ref({ x:0, y:0 })
function lerp(a,b,n){ return (1-n)*a + n*b }

function updateTilt(e){
  const rect = card.value.getBoundingClientRect()
  const cx = rect.width/2
  const cy = rect.height/2
  const dx = e.clientX - rect.left - cx
  const dy = e.clientY - rect.top - cy
  targetTilt.value.x = (dy/cy)*-15
  targetTilt.value.y = (dx/cx)*15
}
function resetTilt(){ targetTilt.value.x = 0; targetTilt.value.y = 0 }

onMounted(()=>{ 
  function animate(){
    tilt.value.x = lerp(tilt.value.x, targetTilt.value.x, 0.15)
    tilt.value.y = lerp(tilt.value.y, targetTilt.value.y, 0.15)
    requestAnimationFrame(animate)
  }
  animate()
})

// Card styles
const cardStyle = computed(() => ({
  transform: `rotateX(${tilt.value.x}deg) rotateY(${tilt.value.y}deg) scale3d(1.03,1.03,1.03)`,
  transition: 'transform 0.05s'
}))
const shadowStyle = computed(() => ({
  boxShadow: `${tilt.value.y*2}px ${tilt.value.x*2}px 60px rgba(255,255,255,0.15)`
}))

// Animate Proficiency
watch(currentSkill, skill=>{
  animatedLevel.value = 0
  let start = 0
  const duration = 700
  const step = 16
  const increment = skill.level / (duration/step)
  function anim(){
    start += increment
    if(start < skill.level){
      animatedLevel.value = Math.floor(start)
      requestAnimationFrame(anim)
    } else {
      animatedLevel.value = skill.level
    }
  }
  anim()
})

// Navigation
function nextCard(){ currentIndex.value = (currentIndex.value+1)%filteredSkills.value.length }
function prevCard(){ currentIndex.value = (currentIndex.value-1+filteredSkills.value.length)%filteredSkills.value.length }
function switchTab(tabId){ currentTab.value = tabId; currentIndex.value = 0 }
</script>

<style scoped>
/* Card swipe animations */
.card-swipe-enter-active { animation: card-enter 0.6s cubic-bezier(.65,.05,.36,1); }
.card-swipe-leave-active { animation: card-leave 0.5s cubic-bezier(.65,.05,.36,1); }
@keyframes card-enter { 0% { transform: translateY(40px) scale(0.9); opacity:0 } 60% { transform: translateY(-10px) scale(1.05); opacity:1 } 100% { transform: translateY(0px) scale(1); opacity:1 } }
@keyframes card-leave { 0% { transform: translateY(0) scale(1); opacity:1 } 100% { transform: translateY(-30px) scale(0.9); opacity:0 } }

/* Tag fade animation */
.tag-fade-enter-active { transition: all 0.5s ease-out; }
.tag-fade-enter-from { opacity:0; transform: translateY(10px); }
.tag-fade-enter-to { opacity:1; transform: translateY(0); }

/* Background pulse */
.animate-pulse-slow { animation: pulse-slow 6s ease-in-out infinite; }
@keyframes pulse-slow { 0%,100% {opacity:0.3; transform:scale(1);} 50% {opacity:0.5; transform:scale(1.1);} }

/* Icon pulse */
@keyframes pulse-icon { 0%,100% { transform: scale(1); } 50% { transform: scale(1.05); } }
.animate-pulse-icon { animation: pulse-icon 2s ease-in-out infinite; }

/* Expert badge bounce */
@keyframes bounce-slow { 0%,100% {transform: translateY(0);} 50% {transform: translateY(-5px);} }
.animate-bounce-slow { animation: bounce-slow 2s ease-in-out infinite; }

/* Ambient moving lights */
@keyframes light-move {
  0% { transform: translate(0,0) scale(1); opacity:0.3; }
  50% { transform: translate(20px, -30px) scale(1.1); opacity:0.5; }
  100% { transform: translate(0,0) scale(1); opacity:0.3; }
}
.animate-light-move { animation: light-move 8s ease-in-out infinite; }
</style>

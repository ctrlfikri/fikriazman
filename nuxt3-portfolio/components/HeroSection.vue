<template>
  <section class="relative min-h-[70vh] flex flex-col justify-center items-center bg-black overflow-hidden font-sans">
    <!-- Perspective Zooming Grid -->
    <div class="absolute inset-0 z-0 pointer-events-none">
      <div class="grid-perspective"></div>
    </div>

  <!-- Fade only when overlay appears/disappears -->
  <transition name="fade">
    <div
      v-if="showFlash"
      class="absolute inset-0 z-10"
      :style="{
        backgroundImage: `url(${currentImage})`,
        backgroundSize: 'cover',
        backgroundPosition: 'center'
      }"
    >
      <div class="absolute inset-0 bg-black/85"></div>
    </div>
  </transition>


    <!-- Content -->
    <div class="relative z-20 w-full text-center">
      <h1 class="text-6xl md:text-7xl font-bold tracking-tight text-white mb-8 leading-tight">
        I'm a&nbsp;
        <span class="inline-block">
          {{ scrambledText }}
        </span>
      </h1>
      <p class="text-2xl md:text-4xl text-white">
        it's just that
        <span
          class="holo-foil animate-holo-foil cursor-pointer"
          @mouseenter="startFlash"
          @mouseleave="stopFlash"
        >simple.</span>
      </p>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const images = [
  '/news.png',
  '/news-1.png',
  '/news-2.png'
]

const currentImage = ref(images[0])
const showFlash = ref(false)
let flashInterval = null
let idx = 0

function startFlash() {
  showFlash.value = true
  idx = 0
  if (flashInterval) clearInterval(flashInterval)
  flashInterval = setInterval(() => {
    currentImage.value = images[idx % images.length]
    idx++
  }, 300)
}

function stopFlash() {
  showFlash.value = false
  if (flashInterval) clearInterval(flashInterval)
  idx = 0
}

// Scrambling text effect logic
const roles = [
  'Graphic Designer',
  'Video Editor',
  'Web Developer',
  'IT Support'
]
const scrambledText = ref(roles[0])
let roleIdx = 0
let scrambleInterval = null

function scrambleToNextRole() {
  const nextRole = roles[(roleIdx + 1) % roles.length]
  let frame = 0
  const maxFrames = 20
  scrambleInterval = setInterval(() => {
    scrambledText.value = scrambleString(nextRole, frame / maxFrames)
    frame++
    if (frame > maxFrames) {
      scrambledText.value = nextRole
      clearInterval(scrambleInterval)
      roleIdx = (roleIdx + 1) % roles.length
      setTimeout(scrambleToNextRole, 1200)
    }
  }, 50)
}

function scrambleString(target, progress) {
  const chars = '!@#$%^&'
  return target.split('').map((c, i) => {
    if (Math.random() > progress) {
      return chars[Math.floor(Math.random() * chars.length)]
    }
    return c
  }).join('')
}

onMounted(() => {
  setTimeout(scrambleToNextRole, 1200)
})

onBeforeUnmount(() => {
  if (flashInterval) clearInterval(flashInterval)
  if (scrambleInterval) clearInterval(scrambleInterval)
})
</script>

<style scoped>
/* Perspective grid using CSS (unchanged) */
.grid-perspective {
  position: absolute;
  inset: 0;
  width: 100vw;
  height: 100vh;
  pointer-events: none;
  perspective: 800px;
}
.grid-perspective::before,
.grid-perspective::after {
  content: "";
  position: absolute;
  left: 50%; top: 50%;
  width: 160vw; height: 160vw;
  transform: translate(-50%, -50%) rotateX(65deg) scaleY(0.7) scaleX(1.1);
  background-image:
    repeating-linear-gradient(transparent, transparent 38px, #ffe60022 39px, transparent 40px),
    repeating-linear-gradient(90deg, transparent, transparent 38px, #ffe60022 39px, transparent 40px);
  opacity: 0.9;
  z-index: 1;
  animation: gridZoom 6s linear infinite;
}
@keyframes gridZoom {
  0% { background-size: 40px 40px, 40px 40px; }
  100% { background-size: 80px 80px, 80px 80px; }
}

/* Holographic foil effect for "simple." */
.holo-foil {
  background: linear-gradient(
    120deg,
    #ff00cc 0%,
    #00ccff 20%,
    #00ffcc 40%,
    #ffe600 60%,
    #ff6600 80%,
    #ff00cc 100%
  );
  background-size: 300% 300%;
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
  -webkit-text-fill-color: transparent;
  letter-spacing: 2px;
  position: relative;
}
@keyframes holo-foil {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}
.animate-holo-foil {
  animation: holo-foil 2.5s linear infinite alternate;
}

/* Typing cursor style */
.typing-cursor {
  display: inline-block;
  width: 1ch;
  animation: blink 1s steps(2, start) infinite;
}
@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from {
  opacity: 0;
}
.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}
.fade-leave-to {
  opacity: 0;
}


</style>

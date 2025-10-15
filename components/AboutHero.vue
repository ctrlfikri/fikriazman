<template>
  <section
    ref="hero"
    class="relative w-full py-12 bg-black text-white flex items-center justify-center overflow-hidden"
    @mousemove="handleMouseMove"
    @mouseleave="resetTilt"
  >
    <!-- Layered Warp Lines -->
    <div
      v-for="depth in 3"
      :key="depth"
      class="absolute inset-0 overflow-hidden"
      :style="{ transform: `translateZ(${depth * 10}px)` }"
    >
      <div
        v-for="i in 40"
        :key="`${depth}-${i}`"
        class="warp-line"
        :style="{
          left: `${Math.random() * 100}%`,
          transform: `rotate(${Math.random() * 40 - 20}deg)`,
          animationDuration: `${3 + Math.random() * 3}s`,
          animationDelay: `${Math.random() * 3}s`,
          opacity: `${0.05 + Math.random() * 0.1}`,
        }"
      ></div>
    </div>

    <!-- Hero Content -->
    <div
      class="relative z-20 text-center px-6 max-w-4xl transition-transform duration-300"
      :style="{
        transform: `rotateX(${tiltY}deg) rotateY(${tiltX}deg)`,
      }"
    >
      <h1
        class="text-4xl md:text-6xl font-extrabold tracking-tight leading-tight mb-6 shiny-text"
      >
        An adaptable IT generalist who blends logic, creativity, and reliability —
        turning complex ideas into simple, working experiences.
      </h1>
      <p
        class="text-white/60 text-lg md:text-xl max-w-2xl mx-auto leading-relaxed"
      >
        From frontend finesse to backend precision, I enjoy bridging design and
        technology to make ideas real.
      </p>
    </div>

    <!-- Subtle cinematic glow -->
    <div
      class="absolute inset-0 bg-gradient-to-b from-black via-transparent to-black pointer-events-none"
    ></div>
    <div
      class="absolute inset-0 bg-[radial-gradient(circle_at_center,rgba(255,255,255,0.05)_0%,transparent_70%)] pointer-events-none"
    ></div>
  </section>
</template>

<script setup>
import { ref } from "vue"

const tiltX = ref(0)
const tiltY = ref(0)
const hero = ref(null)

const handleMouseMove = (e) => {
  if (!hero.value) return
  const rect = hero.value.getBoundingClientRect()
  const x = e.clientX - rect.left
  const y = e.clientY - rect.top
  const midX = rect.width / 2
  const midY = rect.height / 2

  const rotateX = ((y - midY) / midY) * 5
  const rotateY = ((x - midX) / midX) * -5

  tiltX.value = rotateY.toFixed(2)
  tiltY.value = rotateX.toFixed(2)
}

const resetTilt = () => {
  tiltX.value = 0
  tiltY.value = 0
}
</script>

<style scoped>
/* Warp lines animation */
.warp-line {
  position: absolute;
  top: -10%;
  width: 1px;
  height: 20vh;
  background: white;
  opacity: 0.1;
  animation: warpMove linear infinite;
}

@keyframes warpMove {
  0% {
    transform: translateY(100vh) scaleY(0.5);
    opacity: 0;
  }
  15% {
    opacity: 0.15;
  }
  85% {
    opacity: 0.15;
  }
  100% {
    transform: translateY(-20vh) scaleY(1.2);
    opacity: 0;
  }
}

/* Shiny gradient text */
.shiny-text {
  background: linear-gradient(90deg, #ffffff, #bfbfbf, #ffffff, #e5e7eb);
  background-size: 300%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: shine 5s linear infinite;
  letter-spacing: -0.01em;
}

@keyframes shine {
  0% {
    background-position: 0% 50%;
  }
  100% {
    background-position: 300% 50%;
  }
}

/* Fade vignette */
section::before {
  content: "";
  position: absolute;
  inset: 0;
  background: radial-gradient(circle at center, transparent 0%, black 85%);
  pointer-events: none;
}
</style>

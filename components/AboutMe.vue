<template>
  <section class="relative w-full bg-black text-white overflow-hidden py-28 sm:py-32 lg:py-40">
    <!-- Subtle animated grid background -->
    <canvas ref="gridCanvas" class="absolute inset-0 w-full h-full opacity-10 z-[5] pointer-events-none"></canvas>

    <div
      class="relative z-10 max-w-7xl mx-auto px-6 lg:px-8 grid grid-cols-1 lg:grid-cols-2 gap-20 items-center"
    >
      <!-- Text section -->
      <div>
        <h2
          class="text-4xl sm:text-5xl lg:text-6xl font-semibold tracking-tight mb-8 bg-gradient-to-r from-white to-gray-400 bg-clip-text text-transparent"
        >
          About Me
        </h2>

        <div class="space-y-6 text-gray-300 text-lg leading-relaxed max-w-xl">
          <p>
            I'm a designer and front-end developer passionate about bridging creativity and logic. What started as
            making simple posters evolved into crafting interactive digital experiences that connect people and ideas.
          </p>
          <p>
            I'm currently seeking real-world opportunities where I can collaborate, learn, and contribute to
            building experiences that are not only beautiful but also purposeful. I value clean design, thoughtful
            code, and teamwork that drives meaningful results.
          </p>
        </div>

        <div class="mt-10 flex flex-wrap gap-3">
          <span class="px-4 py-1.5 bg-white/5 border border-white/10 text-sm rounded-full"> Designer </span>
          <span class="px-4 py-1.5 bg-white/5 border border-white/10 text-sm rounded-full"> Frontend Developer </span>
          <span class="px-4 py-1.5 bg-white/5 border border-white/10 text-sm rounded-full"> Visual Thinker </span>
        </div>

        <div class="mt-12">
          <NuxtLink
            to="/about"
            class="inline-block px-6 py-3 rounded-xl bg-white text-black font-medium hover:bg-gray-200 transition-all duration-300"
          >
            Read Full Story →
          </NuxtLink>
        </div>
      </div>

      <!-- IMAGE SECTION -->
      <div class="relative flex justify-center lg:justify-end">
        
        <!-- Desktop Image -->
        <div
          class="hidden lg:block relative w-72 sm:w-80 lg:w-[420px] overflow-hidden shadow-2xl border border-white/10 bg-white/5"
        >
        
          <!-- Minimal corner accents -->
          <div class="absolute top-0 left-0 w-12 h-12 border-t-2 border-l-2 border-white/20"></div>
          <div class="absolute top-0 right-0 w-12 h-12 border-t-2 border-r-2 border-white/20"></div>
          <div class="absolute bottom-0 left-0 w-12 h-12 border-b-2 border-l-2 border-white/20"></div>
          <div class="absolute bottom-0 right-0 w-12 h-12 border-b-2 border-r-2 border-white/20"></div>

          <img
            src="/panjat.webp"
            alt="Fikri Azman portrait"
            class="object-contain object-center w-full h-full transition duration-700 ease-in-out"
            loading="lazy"
          />
          <div class="absolute inset-0 bg-gradient-to-tr from-black/40 to-transparent pointer-events-none"></div>
        </div>

        <!-- Mobile / Tablet background image -->
        <img
          src="/panjat.webp"
          alt="Fikri Azman portrait background"
          class="lg:hidden absolute right-[-10%] top-1/2 -translate-y-1/2 w-[120%] opacity-25 blur-sm object-contain pointer-events-none z-[1] transition-transform duration-700 ease-in-out"
          loading="lazy"
        />
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted, ref } from 'vue'

const gridCanvas = ref(null)

onMounted(() => {
  const canvas = gridCanvas.value
  const ctx = canvas.getContext('2d')

  const resize = () => {
    canvas.width = canvas.offsetWidth
    canvas.height = canvas.offsetHeight
  }

  resize()
  window.addEventListener('resize', resize)

  const gridSize = 80
  const dot = {
    x: Math.random() * canvas.width,
    y: Math.random() * canvas.height,
    vx: 0.25,
    vy: 0.25
  }

  const drawGrid = () => {
    ctx.strokeStyle = 'rgba(255,255,255,0.12)'
    ctx.lineWidth = 1
    for (let x = 0; x < canvas.width; x += gridSize) {
      ctx.beginPath()
      ctx.moveTo(x, 0)
      ctx.lineTo(x, canvas.height)
      ctx.stroke()
    }
    for (let y = 0; y < canvas.height; y += gridSize) {
      ctx.beginPath()
      ctx.moveTo(0, y)
      ctx.lineTo(canvas.width, y)
      ctx.stroke()
    }
  }

  const drawDot = () => {
    ctx.shadowBlur = 16
    ctx.shadowColor = 'white'
    ctx.fillStyle = 'rgba(255,255,255,0.9)'
    ctx.beginPath()
    ctx.arc(dot.x, dot.y, 2.5, 0, Math.PI * 2)
    ctx.fill()
    ctx.shadowBlur = 0
  }

  const animate = () => {
    // Faint trail background
    ctx.fillStyle = 'rgba(0,0,0,0.1)'
    ctx.fillRect(0, 0, canvas.width, canvas.height)

    // Draw grid & dot
    drawGrid()
    drawDot()

    // Update position
    dot.x += dot.vx
    dot.y += dot.vy
    if (dot.x > canvas.width || dot.x < 0) dot.vx *= -1
    if (dot.y > canvas.height || dot.y < 0) dot.vy *= -1

    requestAnimationFrame(animate)
  }

  animate()
})
</script>

<style scoped>
canvas {
  position: absolute;
  inset: 0;
  z-index: 5;
  mix-blend-mode: screen;
  background-color: transparent;
}
</style>
<template>
  <section class="relative w-full bg-black text-white">
    
    <div class="max-w-7xl mx-auto px-6 py-20">

      <div class="space-y-24">
        <!-- Chapter 1: Early Fascination -->
        <div class="grid md:grid-cols-2 gap-12 items-center">
          <div 
            class="order-2 md:order-1 space-y-6"
            :class="{ 'animate-fade-in-up': chapter1Visible }"
            ref="chapter1"
          >
            <div class="inline-block px-4 py-2 bg-blue-500/10 border border-blue-500/20 rounded-full text-blue-400 text-sm font-medium">
              Chapter 1: The Spark
            </div>
            <h3 class="text-3xl font-bold">Where It All Began</h3>
            <p class="text-white/70 text-lg leading-relaxed">
              My fascination with technology started young—at just 9 years old, I was already curious about 
              how computers worked. Not just using them, but understanding the architecture, the logic, 
              the systems beneath the surface. That early exposure planted a seed that would grow into 
              a lifelong passion.
            </p>
            <p class="text-white/70 text-lg leading-relaxed">
              While other kids were playing games, I was trying to figure out how those games were made.
            </p>
          </div>
          <div 
            class="order-1 md:order-2 aspect-square bg-gradient-to-br from-blue-500/20 to-purple-500/20 rounded-2xl border border-white/10 overflow-hidden"
            :class="{ 'animate-fade-in-up': chapter1Visible }"
          >
            <div class="w-full h-full flex items-center justify-center relative">
              <img 
                src="https://images.unsplash.com/photo-1517694712202-14dd9538aa97?w=800&h=800&fit=crop" 
                alt="Young tech enthusiast"
                class="w-full h-full object-cover"
                @error="handleImageError"
              />
              <div class="absolute inset-0 flex items-center justify-center text-white/30 text-6xl font-bold">
                [Your Photo]
              </div>
            </div>
          </div>
        </div>

        <!-- Section Divider -->
        <div class="flex items-center gap-4">
          <div class="h-px flex-1 bg-gradient-to-r from-transparent via-white/20 to-transparent"></div>
          <div class="w-2 h-2 rounded-full bg-white/20"></div>
          <div class="h-px flex-1 bg-gradient-to-r from-transparent via-white/20 to-transparent"></div>
        </div>

        <!-- Chapter 2: Design Discovery -->
        <div class="grid md:grid-cols-2 gap-12 items-center">
          <div 
            class="aspect-square bg-gradient-to-br from-pink-500/20 to-orange-500/20 rounded-2xl border border-white/10 overflow-hidden"
            :class="{ 'animate-fade-in-up': chapter2Visible }"
          >
            <div class="w-full h-full flex items-center justify-center relative">
              <img 
                src="https://images.unsplash.com/photo-1561070791-2526d30994b5?w=800&h=800&fit=crop" 
                alt="Design work"
                class="w-full h-full object-cover"
                @error="handleImageError"
              />
              <div class="absolute inset-0 flex items-center justify-center text-white/30 text-6xl font-bold">
                [Your Photo]
              </div>
            </div>
          </div>
          <div 
            class="space-y-6"
            :class="{ 'animate-fade-in-up': chapter2Visible }"
            ref="chapter2"
          >
            <div class="inline-block px-4 py-2 bg-pink-500/10 border border-pink-500/20 rounded-full text-pink-400 text-sm font-medium">
              Chapter 2: The Creative Spark
            </div>
            <h3 class="text-3xl font-bold">Discovering Design</h3>
            <p class="text-white/70 text-lg leading-relaxed">
              But technology alone wasn't enough. I found myself drawn to the visual world—designing 
              digital assets, crafting websites, creating posters, editing videos. There was something 
              magical about taking an idea and making it <span class="text-white font-semibold italic">look good</span> while 
              making it <span class="text-white font-semibold italic">work perfectly</span>.
            </p>
            <p class="text-white/70 text-lg leading-relaxed">
              That's when it clicked: <span class="text-white font-semibold">computers + design = web development</span>. 
              The perfect intersection of logic and creativity.
            </p>
          </div>
        </div>

        <!-- Section Divider -->
        <div class="flex items-center gap-4">
          <div class="h-px flex-1 bg-gradient-to-r from-transparent via-white/20 to-transparent"></div>
          <div class="w-2 h-2 rounded-full bg-white/20"></div>
          <div class="h-px flex-1 bg-gradient-to-r from-transparent via-white/20 to-transparent"></div>
        </div>

        <!-- Chapter 3: The Realization -->
        <div class="grid md:grid-cols-2 gap-12 items-center">
          <div 
            class="order-2 md:order-1 space-y-6"
            :class="{ 'animate-fade-in-up': chapter3Visible }"
            ref="chapter3"
          >
            <div class="inline-block px-4 py-2 bg-emerald-500/10 border border-emerald-500/20 rounded-full text-emerald-400 text-sm font-medium">
              Chapter 3: The Vision
            </div>
            <h3 class="text-3xl font-bold">Engineering Meets Artistry</h3>
            <p class="text-white/70 text-lg leading-relaxed">
              Websites became my canvas. On one side, you have the TCP/IP model, protocols, databases, 
              APIs—the engineering foundation. On the other, you have typography, color theory, user 
              experience, visual storytelling—the creative expression.
            </p>
            <p class="text-white/70 text-lg leading-relaxed">
              I realized that in today's digital-first world, <span class="text-white font-semibold">every business 
              has an opportunity to craft a unique online presence</span>. Even the most "bland" business 
              can become memorable with the right blend of functionality and design. That's where I thrive.
            </p>
          </div>
          <div 
            class="order-1 md:order-2 aspect-square bg-gradient-to-br from-emerald-500/20 to-teal-500/20 rounded-2xl border border-white/10 overflow-hidden"
            :class="{ 'animate-fade-in-up': chapter3Visible }"
          >
            <div class="w-full h-full flex items-center justify-center relative">
              <img 
                src="https://images.unsplash.com/photo-1498050108023-c5249f4df085?w=800&h=800&fit=crop" 
                alt="Coding and design"
                class="w-full h-full object-cover"
                @error="handleImageError"
              />
              <div class="absolute inset-0 flex items-center justify-center text-white/30 text-6xl font-bold">
                [Your Photo]
              </div>
            </div>
          </div>
        </div>

        <!-- Section Divider -->
        <div class="flex items-center gap-4">
          <div class="h-px flex-1 bg-gradient-to-r from-transparent via-white/20 to-transparent"></div>
          <div class="w-2 h-2 rounded-full bg-white/20"></div>
          <div class="h-px flex-1 bg-gradient-to-r from-transparent via-white/20 to-transparent"></div>
        </div>

        <!-- Chapter 4: Ready for Impact -->
        <div class="text-center max-w-3xl mx-auto space-y-6">
          <div class="inline-block px-4 py-2 bg-purple-500/10 border border-purple-500/20 rounded-full text-purple-400 text-sm font-medium">
            Chapter 4: Ready to Scale
          </div>
          <h3 class="text-3xl md:text-4xl font-bold">Now, I'm Ready for More</h3>
          <p class="text-white/70 text-lg leading-relaxed">
            I've spent years honing my craft, building projects, and pushing myself to learn more. 
            But now I'm ready to take the next step—to be part of something bigger. 
          </p>
          <p class="text-white/70 text-lg leading-relaxed">
            I want to pour my passion into larger projects, contribute to ambitious teams, and help 
            businesses stand out in the digital landscape. Not just to advance my career, but to create 
            real impact for the companies and people I work with.
          </p>
          <div class="pt-6">
            <blockquote class="text-2xl font-semibold italic text-white/90 border-l-4 border-white/30 pl-6">
              "I'm not just looking for a job—I'm looking for a mission to be part of."
            </blockquote>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const chapter1 = ref(null)
const chapter2 = ref(null)
const chapter3 = ref(null)
const chapter1Visible = ref(false)
const chapter2Visible = ref(false)
const chapter3Visible = ref(false)

const handleImageError = (e) => {
  e.target.style.display = 'none'
}

onMounted(() => {
  const observerOptions = {
    threshold: 0.2,
    rootMargin: '0px'
  }

  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        if (entry.target === chapter1.value) chapter1Visible.value = true
        if (entry.target === chapter2.value) chapter2Visible.value = true
        if (entry.target === chapter3.value) chapter3Visible.value = true
      }
    })
  }, observerOptions)

  if (chapter1.value) observer.observe(chapter1.value)
  if (chapter2.value) observer.observe(chapter2.value)
  if (chapter3.value) observer.observe(chapter3.value)
})
</script>

<style scoped>
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in-up {
  animation: fadeInUp 0.8s ease-out forwards;
}
</style>
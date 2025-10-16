<template>
  <main class="min-h-screen bg-black text-white">
    <section class="max-w-7xl mx-auto px-6 py-20">
      <!-- Grid Container -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 auto-rows-[320px]">
        
        <!-- Project 1: Dareia Coffee - Large Card (spans 2 columns on lg) -->
        <NuxtLink
          to="/projects/dareia-coffee"
          class="group relative lg:col-span-2 row-span-2 bg-gradient-to-br from-blue-600 to-blue-800 border border-white/10 rounded-3xl overflow-hidden hover:border-blue-400/50 transition-all duration-500 hover:scale-[1.02]"
        >
          <!-- Animated Background -->
          <div class="absolute inset-0 opacity-20">
            <div
              v-for="i in 15"
              :key="`bubble-${i}`"
              class="absolute rounded-full bg-white animate-bubble-float"
              :style="{
                width: `${Math.random() * 60 + 20}px`,
                height: `${Math.random() * 60 + 20}px`,
                left: `${Math.random() * 100}%`,
                top: `${100 + Math.random() * 20}%`,
                animationDelay: `${Math.random() * 8}s`,
                animationDuration: `${Math.random() * 8 + 10}s`,
              }"
            />
          </div>

          <!-- Content -->
          <div class="relative h-full p-8 flex flex-col justify-between">
            <div>
              <div class="inline-block px-4 py-2 bg-white/20 border border-white/30 rounded-full text-xs font-bold text-white mb-4">
                GRAPHIC DESIGN
              </div>
              <img src="/dclogo.png" alt="Dareia Coffee" class="h-20 mb-4 drop-shadow-2xl" />
              <h2 class="text-4xl lg:text-5xl font-black mb-3 text-white group-hover:text-blue-200 transition-colors">
                Dareia Coffee
              </h2>
              <p class="text-white/80 text-lg mb-4 max-w-md">
                Crafted Banners, Flyers, Menu Panels, Social Media Posters, and Campaign Visuals.
              </p>
            </div>

            <!-- Tech Stack Pills -->
            <div class="flex flex-wrap gap-2">
              <span class="px-3 py-1 bg-white/10 backdrop-blur-sm rounded-full text-xs font-medium">Photoshop</span>
              <span class="px-3 py-1 bg-white/10 backdrop-blur-sm rounded-full text-xs font-medium">Canva</span>
              <span class="px-3 py-1 bg-white/10 backdrop-blur-sm rounded-full text-xs font-medium">Illustrator</span>
            </div>

            <!-- Hover Arrow -->
            <div class="absolute top-8 right-8 w-12 h-12 bg-white/10 backdrop-blur-sm rounded-full flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
              </svg>
            </div>
          </div>

          <!-- Subtle Image Preview -->
          <div class="absolute bottom-0 right-0 w-64 h-64 opacity-20 group-hover:opacity-30 transition-opacity">
            <img src="/coffees.png" alt="Coffee" class="w-full h-full object-contain" />
          </div>
        </NuxtLink>

        <!-- Project 2: CTRLPC - Tall Card -->
        <NuxtLink
          to="/projects/ctrlpc"
          class="group relative row-span-2 bg-gradient-to-br from-cyan-500 to-teal-600 border border-white/10 rounded-3xl overflow-hidden hover:border-cyan-400/50 transition-all duration-500 hover:scale-[1.02]"
        >
          <!-- Tech Grid Background -->
          <div class="absolute inset-0 opacity-20 tech-grid" />
          
          <!-- Scanning Line -->
          <div class="absolute inset-0">
            <div class="absolute h-px w-full bg-gradient-to-r from-transparent via-cyan-400 to-transparent animate-scan-horizontal top-1/2" />
          </div>

          <!-- Content -->
          <div class="relative h-full p-8 flex flex-col justify-between">
            <div>
              <div class="inline-block px-4 py-2 bg-white/20 border border-white/30 rounded-full text-xs font-bold text-white mb-4">
                CONTENT CREATION & VIDEO EDITOR
              </div>
              <img src="/ctrlpclogo.png" alt="CTRLPC" class="h-16 mb-4 drop-shadow-2xl" />
              <h2 class="text-3xl font-black mb-3 text-white group-hover:text-cyan-200 transition-colors">
                CTRLPC
              </h2>
              <p class="text-white/80 mb-4">
                Create Engaging Short-Form Content about the PC Hardware and Hardware Reviews.
              </p>
            </div>

            <!-- Tech Stack Pills -->
            <div class="flex flex-wrap gap-2">
              <span class="px-3 py-1 bg-white/10 backdrop-blur-sm rounded-full text-xs font-medium">Capcut</span>
              <span class="px-3 py-1 bg-white/10 backdrop-blur-sm rounded-full text-xs font-medium">Sony Vegas Pro</span>
            </div>

            <!-- Hover Arrow -->
            <div class="absolute top-8 right-8 w-12 h-12 bg-white/10 backdrop-blur-sm rounded-full flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity duration-300">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
              </svg>
            </div>
          </div>
        </NuxtLink>

        <!-- Project 3: Progscale - Wide Card -->
        <NuxtLink
        to="/projects/progscale"
        class="group relative md:col-span-2 lg:col-span-3 bg-gradient-to-br from-emerald-100 to-teal-50 border border-white/10 rounded-3xl overflow-hidden hover:border-emerald-400/50 transition-all duration-500 hover:scale-[1.02]"
        >
        <!-- Code Particles Background -->
        <div class="absolute inset-0 overflow-hidden opacity-20">
            <div
            v-for="i in 20"
            :key="`particle-${i}`"
            class="absolute animate-code-float font-mono font-bold text-emerald-600/60"
            :style="{
                left: `${Math.random() * 100}%`,
                top: `${Math.random() * 100}%`,
                fontSize: `${Math.random() * 20 + 12}px`,
                animationDelay: `${Math.random() * 5}s`,
                animationDuration: `${Math.random() * 15 + 15}s`,
            }"
            >
            {{ ['{ }', '< >', '[ ]', '( )', '/>', '==', '=>', '++'][Math.floor(Math.random() * 8)] }}
            </div>
        </div>

        <!-- Image Preview - Positioned absolutely on the right -->
        <div class="hidden lg:block absolute right-8 top-1/2 -translate-y-1/2 w-72 xl:w-96 opacity-20 group-hover:opacity-40 transition-all duration-500 pointer-events-none">
            <img src="/hihi.png" alt="Progscale Preview" class="w-full h-auto object-contain drop-shadow-2xl" />
        </div>

        <!-- Content -->
        <div class="relative p-8 lg:p-12">
            <div class="max-w-2xl">
            <div class="inline-block px-4 py-2 bg-teal-600/30 border border-teal-700/50 rounded-full text-xs font-bold text-teal-900 mb-4 uppercase tracking-wider">
                WEB DESIGN
            </div>
            
            <img src="/progscalelogo.png" alt="Progscale" class="h-12 lg:h-14 mb-4 drop-shadow-lg" />
            
            <h2 class="text-3xl lg:text-4xl font-black mb-3 text-teal-900 group-hover:text-teal-700 transition-colors">
                Progscale
            </h2>
            
            <p class="text-teal-900/80 text-base lg:text-lg mb-6 leading-relaxed">
                Built scalable solutions for modern web applications with cutting-edge technology.
            </p>

            <!-- Tech Stack Pills -->
            <div class="flex flex-wrap gap-2">
                <span class="px-3 py-1.5 bg-teal-600/20 backdrop-blur-sm rounded-full text-xs font-semibold text-teal-900 border border-teal-600/20">Vue</span>
                <span class="px-3 py-1.5 bg-teal-600/20 backdrop-blur-sm rounded-full text-xs font-semibold text-teal-900 border border-teal-600/20">Photoshop</span>
                <span class="px-3 py-1.5 bg-teal-600/20 backdrop-blur-sm rounded-full text-xs font-semibold text-teal-900 border border-teal-600/20">Canva</span>
                <span class="px-3 py-1.5 bg-teal-600/20 backdrop-blur-sm rounded-full text-xs font-semibold text-teal-900 border border-teal-600/20">Wordpress</span>
            </div>
            </div>
        </div>

        <!-- Hover Arrow -->
        <div class="absolute top-8 right-8 w-12 h-12 bg-teal-600/30 backdrop-blur-sm rounded-full flex items-center justify-center opacity-0 group-hover:opacity-100 transition-all duration-300 group-hover:scale-110">
            <svg class="w-6 h-6 text-teal-900" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
            </svg>
        </div>
        </NuxtLink>

        <!-- Info Card - Stats -->
        <div class="relative bg-gradient-to-br from-purple-900/40 to-pink-900/40 border border-white/10 rounded-3xl p-8 overflow-hidden">
          <div class="relative z-10">
            <div class="text-5xl font-black mb-2 bg-gradient-to-r from-purple-400 to-pink-400 bg-clip-text text-transparent">
              3+
            </div>
            <div class="text-white/70 font-semibold">Major Projects</div>
            <div class="mt-4 text-sm text-white/50">
              Excluding freelance work
            </div>
          </div>
          
          <!-- Decorative element -->
          <div class="absolute -bottom-4 -right-4 w-32 h-32 bg-gradient-to-br from-purple-500/20 to-pink-500/20 rounded-full blur-3xl" />
        </div>

        <!-- Info Card - Role -->
        <div class="relative bg-gradient-to-br from-blue-900/40 to-indigo-900/40 border border-white/10 rounded-3xl p-8 overflow-hidden">
          <div class="relative z-10">
            <div class="text-4xl mb-4">💼</div>
            <div class="text-xl font-bold mb-2">Multi-Disciplinary</div>
            <div class="text-white/60 text-sm">
              Design • Development • Content Creation
            </div>
          </div>
          
          <!-- Decorative element -->
          <div class="absolute -top-4 -left-4 w-32 h-32 bg-gradient-to-br from-blue-500/20 to-indigo-500/20 rounded-full blur-3xl" />
        </div>

        <!-- CTA Card -->
        <div class="relative bg-gradient-to-br from-white/5 to-white/0 border border-white/10 rounded-3xl p-8 overflow-hidden hover:border-white/30 transition-all duration-300 group cursor-pointer">
          <div class="relative z-10 h-full flex flex-col justify-between">
            <div>
              <div class="text-4xl mb-4">✨</div>
              <div class="text-xl font-bold mb-2">Want to collaborate?</div>
              <div class="text-white/60 text-sm">
                Let's build something amazing together
              </div>
            </div>
            
            <div class="flex items-center gap-2 text-white/80 group-hover:text-white transition-colors mt-4">
              Get in touch
              <svg class="w-4 h-4 group-hover:translate-x-1 transition-transform" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
              </svg>
            </div>
          </div>
        </div>

      </div>
    </section>
  </main>
</template>

<script setup>

</script>

<style scoped>
/* Bubble Float Animation */
@keyframes bubble-float {
  0% {
    transform: translateY(0) scale(0.8);
    opacity: 0;
  }
  10% {
    opacity: 0.15;
  }
  90% {
    opacity: 0.1;
  }
  100% {
    transform: translateY(-120vh) scale(1.2);
    opacity: 0;
  }
}

.animate-bubble-float {
  animation: bubble-float linear infinite;
}

/* Tech Grid */
.tech-grid {
  background-image: 
    linear-gradient(rgba(34, 211, 238, 0.3) 1px, transparent 1px),
    linear-gradient(90deg, rgba(34, 211, 238, 0.3) 1px, transparent 1px);
  background-size: 40px 40px;
  animation: grid-move 10s linear infinite;
}

@keyframes grid-move {
  0% { background-position: 0 0; }
  100% { background-position: 40px 40px; }
}

/* Scan Horizontal */
@keyframes scan-horizontal {
  0% { transform: translateX(-100%); }
  100% { transform: translateX(200vw); }
}

.animate-scan-horizontal {
  animation: scan-horizontal 8s linear infinite;
}

/* Code Float */
@keyframes code-float {
  0% {
    transform: translate(0, 0) rotate(0deg);
    opacity: 0;
  }
  10% {
    opacity: 0.6;
  }
  90% {
    opacity: 0.3;
  }
  100% {
    transform: translate(
      calc(-50px + 100px * var(--random, 0.5)),
      -100vh
    ) rotate(360deg);
    opacity: 0;
  }
}

.animate-code-float {
  animation: code-float linear infinite;
}
</style>
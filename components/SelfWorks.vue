<template>
  <section class="max-w-7xl mx-auto px-6 py-24 bg-gradient-to-b from-black via-[#0a0a0f] to-[#050507]">
    <!-- Bento Grid -->
    <div
      class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-6 auto-rows-[320px] md:auto-rows-[340px]"
    >
      <!-- 🧠 Project 1: AI Trading Website -->
      <NuxtLink
        to="/projects/ai-trading"
        class="group relative col-span-1 sm:col-span-2 row-span-2 bg-gradient-to-br from-[#0e0e11] to-[#14141a] border border-[#1f1f25] rounded-3xl overflow-hidden hover:border-[#00ff8844] transition-all duration-700 hover:scale-[1.03] hover:shadow-[0_0_40px_#00ff8844]"
      >
        <!-- Neural Glow Nodes -->
        <div class="absolute inset-0 overflow-hidden opacity-20">
          <div
            v-for="i in 18"
            :key="`node-${i}`"
            class="absolute w-1.5 h-1.5 bg-[#00ff88] rounded-full animate-pulse-glow"
            :style="{
              left: `${Math.random() * 100}%`,
              top: `${Math.random() * 100}%`,
              animationDelay: `${Math.random() * 3}s`,
              boxShadow: '0 0 10px rgba(0,255,136,0.8)'
            }"
          />
        </div>

        <!-- Snapshot Preview -->
        <img
          src="/snapshot-1.png"
          alt="Forex Signal Snapshot"
          class="absolute inset-0 w-full h-full object-cover opacity-20 group-hover:opacity-30 transition duration-700"
        />

        <!-- Content -->
        <div
          class="relative h-full p-10 flex flex-col justify-between transition-transform duration-700 group-hover:translate-y-[-6px]"
        >
          <div>
            <div class="flex items-center gap-2 mb-5">
              <span
                class="px-4 py-1 bg-[#00ff8844] border border-[#00ff8855] rounded-full text-xs font-bold text-[#00ff99]"
              >FULL-STACK</span>
              <span
                class="px-4 py-1 bg-[#00ff8844] border border-[#00ff8855] rounded-full text-xs font-bold text-[#00ff99]"
              >AI/ML</span>
            </div>

            <div class="text-5xl mb-3">🤖</div>
            <h2
              class="text-3xl lg:text-4xl font-black mb-3 text-white group-hover:text-[#00ffb3] transition-colors"
            >
              Full-Stack AI Trading Website
            </h2>
            <p class="text-white/70 leading-relaxed">
              An intelligent trading platform powered by real-time AI models for prediction and automation.
            </p>
          </div>

          <div class="flex flex-wrap gap-2 mt-6 text-xs text-white/80">
            <span class="pill">Next.js</span>
            <span class="pill">Python</span>
            <span class="pill">TensorFlow</span>
            <span class="pill">FastAPI</span>
            <span class="pill">PostgreSQL</span>
          </div>

          <div class="absolute top-8 right-8 w-10 h-10 bg-[#00ff8822] rounded-full flex items-center justify-center opacity-0 group-hover:opacity-100 transition-all duration-300">
            <svg class="w-5 h-5 text-[#00ff99]" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
            </svg>
          </div>
        </div>
      </NuxtLink>

      <!-- 📘 Project 2: Ebook Design -->
      <NuxtLink
        to="/projects/trading-ebook"
        class="group relative col-span-1 sm:col-span-2 row-span-1 bg-gradient-to-br from-[#1a1400] to-[#241a00] border border-[#2c2300] rounded-3xl overflow-hidden hover:border-[#ffb70055] transition-all duration-700 hover:scale-[1.03] hover:shadow-[0_0_40px_#ffb70055]"
      >
        <!-- Floating Pages -->
        <div class="absolute inset-0 overflow-hidden opacity-15">
          <div
            v-for="i in 12"
            :key="`page-${i}`"
            class="absolute bg-[#ffcc00]/40 rounded-sm animate-page-float"
            :style="{
              width: '50px',
              height: '70px',
              left: `${Math.random() * 100}%`,
              top: `${100 + Math.random() * 20}%`,
              transform: `rotate(${Math.random() * 30 - 15}deg)`,
              animationDelay: `${Math.random() * 4}s`,
              animationDuration: `${Math.random() * 8 + 10}s`
            }"
          />
        </div>

        <!-- Ebook Preview -->
        <img
          src="/ebook.png"
          alt="Roadmap Trader Baru"
          class="absolute inset-0 w-full h-full object-contain opacity-20 group-hover:opacity-40 transition duration-700"
        />

        <div
          class="relative h-full p-10 flex flex-col justify-between transition-transform duration-700 group-hover:translate-y-[-6px]"
        >
          <div>
            <div class="inline-block px-4 py-1 bg-[#ffb70033] border border-[#ffb70055] rounded-full text-xs font-bold text-[#ffcc55] mb-3">
              GRAPHIC DESIGN
            </div>

            <div class="text-5xl mb-3">📚</div>
            <h2
              class="text-3xl font-black mb-3 text-white group-hover:text-[#ffcc55] transition-colors"
            >
              Trading Ebook Design
            </h2>
            <p class="text-white/70 leading-relaxed">
              A comprehensive 120-page ebook featuring custom infographics and editorial storytelling.
            </p>
          </div>

          <div class="flex flex-wrap gap-2 mt-5 text-xs text-white/80">
            <span class="pill">InDesign</span>
            <span class="pill">Illustrator</span>
            <span class="pill">Photoshop</span>
          </div>
        </div>
      </NuxtLink>

      <!-- 💡 Info Card: Self-Driven -->
      <div
        class="relative col-span-1 bg-gradient-to-br from-[#12121a] to-[#0d0d12] border border-[#1b1b22] rounded-3xl p-8 hover:scale-[1.02] transition-all duration-500 overflow-hidden"
      >
        <div class="relative z-10">
          <div class="text-4xl mb-4">💡</div>
          <h3 class="text-2xl font-semibold mb-2 text-white">Self-Driven</h3>
          <p class="text-white/60 text-sm leading-relaxed">
            Built independently to explore AI, design, and automation through practical experiments.
          </p>
        </div>
        <div class="absolute -bottom-6 -right-6 w-28 h-28 bg-[#00ff8855] rounded-full blur-3xl" />
      </div>

      <!-- ❤️ Info Card: Passion -->
      <div
        class="relative col-span-1 bg-gradient-to-br from-[#191018] to-[#140b10] border border-[#1f1a20] rounded-3xl p-8 hover:scale-[1.02] transition-all duration-500 overflow-hidden"
      >
        <div class="relative z-10">
          <div class="text-4xl mb-4">🎯</div>
          <h3 class="text-2xl font-semibold mb-2 text-white">Passion Projects</h3>
          <p class="text-white/60 text-sm leading-relaxed">
            Blending AI, design, and financial insights into creative and impactful projects.
          </p>
        </div>
        <div class="absolute -top-6 -left-6 w-28 h-28 bg-[#ff007755] rounded-full blur-3xl" />
      </div>
    </div>
  </section>
</template>

<script setup>
// no logic needed for now
</script>

<style scoped>
@keyframes pulse-glow {
  0%, 100% {
    opacity: 0.3;
    transform: scale(1);
  }
  50% {
    opacity: 1;
    transform: scale(1.4);
  }
}
.animate-pulse-glow {
  animation: pulse-glow 2.5s ease-in-out infinite;
}

@keyframes page-float {
  0% {
    transform: translateY(0) rotate(0deg);
    opacity: 0;
  }
  10% {
    opacity: 0.7;
  }
  90% {
    opacity: 0.3;
  }
  100% {
    transform: translateY(-120vh) rotate(360deg);
    opacity: 0;
  }
}
.animate-page-float {
  animation: page-float linear infinite;
}

/* Reusable pill style */
.pill {
  @apply px-3 py-1 bg-white/10 backdrop-blur-sm rounded-full text-xs font-medium;
}
</style>

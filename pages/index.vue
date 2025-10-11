<template>
  <div class="flex flex-col bg-black">
    <!-- Hero -->
    <div class="w-full bg-black">
      <div class="border border-white/10 w-full max-w-7xl mx-auto px-4">
        <HeroSection />
      </div>
    </div>

    <!-- Skills -->
    <div class="w-full bg-black">
      <div class="max-w-7xl mx-auto px-4">
        <div class="flex flex-col lg:flex-row items-stretch w-full">
          <!-- Left: Section Title -->
          <div class="lg:w-1/3 text-center border border-white/10 p-4 flex flex-col justify-center">
            <div class="relative w-24 h-24 rounded-full overflow-hidden mx-auto mb-6">
              <img
                src="/avatar.jpeg"
                alt="Avatar"
                class="w-full h-full object-cover rounded-full"
              />
              <div
                class="absolute inset-0 rounded-full border-2 border-white/30 glow-animation pointer-events-none"
              ></div>
            </div>

            <h1 class="text-4xl md:text-5xl font-extrabold text-white tracking-wider mb-4">
              My Skills_
            </h1>
            <p class="text-gray-400 text-lg md:text-xl">
              A glance at what I can do and how proficient I am
            </p>
          </div>

          <!-- Right: Skill Cards -->
          <div class="lg:w-2/3 border border-white/10 overflow-hidden">
            <SkillCard />
          </div>
        </div>
      </div>
    </div>

    <!-- Project LED -->
    <div class="w-full bg-black">
      <div class="w-full border border-white/10 py-8 flex justify-center items-center overflow-hidden max-w-7xl mx-auto px-4 relative">
        <!-- LED Dotted Background -->
        <svg class="absolute inset-0 w-full h-full" viewBox="0 0 1200 200" preserveAspectRatio="none">
          <defs>
            <pattern id="led-dots" x="0" y="0" width="10" height="10" patternUnits="userSpaceOnUse">
              <rect x="0" y="0" width="20" height="20" fill="#050505"/>
              <circle cx="10" cy="10" r="2" fill="black" stroke="gray" stroke-width="1" opacity="0.5"/>
            </pattern>
          </defs>
          <rect width="1200" height="200" fill="#000"/>
          <rect width="1200" height="200" fill="url(#led-dots)"/>
        </svg>

        <!-- Text Overlay -->
        <div class="relative flex flex-col items-center justify-center">
          <h1
            class="font-monospace text-yellow-400 text-4xl md:text-6xl font-extrabold whitespace-nowrap glow-text"
          >
            MY PROJECTS
          </h1>
          <p class="mt-2 p-2 text-gray-400 font-monospace text-2xl text-center">
            See what I have been involved in.
          </p>
        </div>
      </div>
    </div>

    <!-- Projects (Carousel Hero Style) -->
    <div class="w-full bg-black">
      <div class="max-w-7xl mx-auto px-4">
        <ProjectCard />
      </div>
    </div>
  </div>
</template>

<script setup>
import HeroSection from '@/components/HeroSection.vue'
import SkillCard from '@/components/SkillCard.vue'
import ProjectCard from '@/components/ProjectCard.vue'
</script>

<style scoped>
@keyframes pulse-glow {
  0% {
    box-shadow: 0 0 5px 2px rgba(255, 255, 255, 0.3),
      0 0 10px 5px rgba(255, 255, 255, 0.2);
  }
  50% {
    box-shadow: 0 0 15px 5px rgba(255, 255, 255, 0.6),
      0 0 25px 10px rgba(255, 255, 255, 0.4);
  }
  100% {
    box-shadow: 0 0 5px 2px rgba(255, 255, 255, 0.3),
      0 0 10px 5px rgba(255, 255, 255, 0.2);
  }
}

.glow-animation {
  animation: pulse-glow 2s ease-in-out infinite;
}

/* Blinking LED effect */
@keyframes blink {
  0%, 49% { opacity: 1; }
  50%, 100% { opacity: 0.2; }
}
.animate-blink {
  animation: blink 1s step-start infinite;
}

.glow-text {
  animation: blink 1.5s infinite;
}
</style>
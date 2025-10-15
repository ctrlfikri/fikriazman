<template>
  <section class="relative w-full min-h-screen bg-black text-white px-6 py-24 md:py-32 overflow-hidden">
    <!-- Animated Globe Background -->
    <div class="absolute bottom-[-200px] md:bottom-[-400px] left-1/2 -translate-x-1/2 w-[600px] h-[600px] md:w-[1000px] md:h-[1000px] opacity-30 pointer-events-none">
      <div class="globe-container">
        <div class="globe"></div>
      </div>
    </div>

    <div class="max-w-6xl mx-auto relative z-10">
      
      <!-- Minimal Header -->
      <div class="mb-24 md:mb-32">
        <h1 class="text-4xl md:text-6xl font-light tracking-tight mb-3">
          Education
        </h1>
        <div class="w-12 h-px bg-white/20"></div>
      </div>

      <div class="grid md:grid-cols-12 gap-12 md:gap-20">
        
        <!-- Timeline Years -->
        <div class="md:col-span-4">
          <div class="md:sticky md:top-32 space-y-2">
            <button
              v-for="(edu, index) in educationList"
              :key="index"
              @click="activeIndex = index"
              class="group w-full text-left py-3 px-4 transition-all duration-300 rounded-lg"
              :class="activeIndex === index ? 'bg-white/5' : ''"
            >
              <div class="flex items-center justify-between">
                <span 
                  class="text-lg font-light transition-all duration-300"
                  :class="activeIndex === index ? 'text-white' : 'text-white/30 group-hover:text-white/50'"
                >
                  {{ edu.year }}
                </span>
                <div 
                  class="w-1.5 h-1.5 rounded-full bg-white transition-all duration-300"
                  :class="activeIndex === index ? 'opacity-100 scale-100' : 'opacity-0 scale-50'"
                ></div>
              </div>
            </button>
          </div>
        </div>

        <!-- Content -->
        <div class="md:col-span-8">
          <div class="relative min-h-96">
            <Transition
              enter-active-class="transition-all duration-500 ease-out"
              leave-active-class="transition-all duration-300 ease-in absolute inset-0"
              enter-from-class="opacity-0 translate-y-8"
              enter-to-class="opacity-100 translate-y-0"
              leave-from-class="opacity-100 translate-y-0"
              leave-to-class="opacity-0 -translate-y-4"
              mode="out-in"
            >
              <div
                :key="activeIndex"
                class="space-y-8"
              >
                <!-- Logo & Institution -->
                <div class="flex items-start gap-6">
                  <!-- Logo -->
                  <div class="flex-shrink-0 w-16 h-16 md:w-20 md:h-20 rounded-2xl bg-white/5 backdrop-blur-sm border border-white/10 p-3 flex items-center justify-center overflow-hidden">
                    <img 
                      :src="educationList[activeIndex].logo" 
                      :alt="`${educationList[activeIndex].institution} logo`"
                      class="w-full h-full object-contain opacity-90"
                    />
                  </div>
                  
                  <!-- Text -->
                  <div class="space-y-2 flex-1">
                    <h2 class="text-3xl md:text-4xl font-light tracking-tight">
                      {{ educationList[activeIndex].institution }}
                    </h2>
                    <p class="text-lg md:text-xl text-white/60 font-light">
                      {{ educationList[activeIndex].degree }}
                    </p>
                  </div>
                </div>

                <!-- Description -->
                <p class="text-base md:text-lg text-white/50 leading-relaxed font-light max-w-2xl">
                  {{ educationList[activeIndex].description }}
                </p>

                <!-- Subtle indicator -->
                <div class="flex gap-1.5 pt-4">
                  <div 
                    v-for="i in 3" 
                    :key="i"
                    class="w-1 h-1 rounded-full bg-white/20 animate-pulse"
                    :style="{ animationDelay: `${i * 150}ms` }"
                  ></div>
                </div>
              </div>
            </Transition>
          </div>
        </div>

      </div>

      <!-- Progress Indicator -->
      <div class="flex justify-center gap-2 mt-20 md:mt-32">
        <button
          v-for="(_, index) in educationList"
          :key="index"
          @click="activeIndex = index"
          class="transition-all duration-300"
          :class="activeIndex === index ? 'w-8 h-px bg-white' : 'w-6 h-px bg-white/20 hover:bg-white/40'"
        ></button>
      </div>

    </div>
  </section>
</template>

<script setup lang="ts">
const activeIndex = ref(0)

const educationList = [
  {
    year: "2012 – 2016",
    institution: "Sekolah Dato Abdul Razak",
    degree: "Malaysian Certificate of Education (SPM)",
    description:
      "National boarding school that shaped my discipline and teamwork. Actively participated in volleyball, creative competitions, and leadership roles — building strong soft skills early on.",
    logo: "/sdar.png"
  },
  {
    year: "2017 – 2018",
    institution: "Kolej Matrikulasi Negeri Sembilan",
    degree: "Matriculation Programme (Science Stream)",
    description:
      "Refined logical thinking and adaptability while exploring the bridge between science and technology. This was the foundation of my problem-solving mindset.",
    logo: "/kmns.png"
  },
  {
    year: "2018 – 2022",
    institution: "Universiti Tun Hussein Onn Malaysia",
    degree: "Bachelor of Information Technology (Web Technology) with Honours",
    description:
      "Graduated with honours (GPA 3.19). Among Top 5 Final Year Projects (2021). This is where I discovered my passion for web development, design, and automation — blending creativity with technical execution.",
    logo: "/uthm.png"
  },
]
</script>

<style scoped>
@keyframes pulse {
  0%, 100% { opacity: 0.2; }
  50% { opacity: 0.5; }
}

.animate-pulse {
  animation: pulse 2s ease-in-out infinite;
}

/* Globe Animation */
.globe-container {
  width: 100%;
  height: 100%;
  perspective: 1500px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.globe {
  width: 100%;
  height: 100%;
  border-radius: 50%;
  background: 
    radial-gradient(circle at 35% 35%, rgba(255, 255, 255, 0.15) 0%, transparent 70%),
    radial-gradient(circle, rgba(20, 20, 20, 1) 0%, rgba(0, 0, 0, 0.8) 100%);
  position: relative;
  animation: rotate-globe 50s linear infinite;
  transform-style: preserve-3d;
  border: 2px solid rgba(255, 255, 255, 0.1);
  box-shadow: 
    inset 0 0 100px rgba(0, 0, 0, 0.8),
    inset 20px 0 80px rgba(0, 0, 0, 0.6),
    inset -20px 0 80px rgba(0, 0, 0, 0.6),
    0 0 50px rgba(255, 255, 255, 0.05);
}

.globe::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: 50%;
  background-image: 
    repeating-linear-gradient(
      0deg,
      transparent 0px,
      transparent 45px,
      rgba(255, 255, 255, 0.08) 45px,
      rgba(255, 255, 255, 0.08) 47px,
      transparent 47px
    ),
    repeating-linear-gradient(
      90deg,
      transparent 0px,
      transparent 45px,
      rgba(255, 255, 255, 0.08) 45px,
      rgba(255, 255, 255, 0.08) 47px,
      transparent 47px
    );
  animation: rotate-grid 50s linear infinite reverse;
  mask-image: radial-gradient(circle, black 40%, transparent 70%);
  -webkit-mask-image: radial-gradient(circle, black 40%, transparent 70%);
}

.globe::after {
  content: '';
  position: absolute;
  top: 10%;
  left: 10%;
  width: 30%;
  height: 30%;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.2) 0%, transparent 70%);
  filter: blur(20px);
}

@keyframes rotate-globe {
  from {
    transform: rotateY(0deg) rotateX(15deg);
  }
  to {
    transform: rotateY(360deg) rotateX(15deg);
  }
}

@keyframes rotate-grid {
  from {
    transform: rotateY(0deg);
  }
  to {
    transform: rotateY(-360deg);
  }
}
</style>
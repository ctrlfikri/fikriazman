<template>
  <section class="relative w-full bg-black text-white border-t border-white/10">
    <div class="max-w-7xl mx-auto px-6 py-20">
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold mb-4">How I Work</h2>
        <p class="text-white/60 text-lg max-w-2xl mx-auto">
          A proven methodology that consistently delivers results
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <div
          v-for="(item, idx) in approach"
          :key="idx"
          class="group relative p-8 bg-gradient-to-br from-white/5 to-transparent border border-white/10 rounded-2xl hover:border-white/30 transition-all duration-500 hover:scale-105"
        >
          <div class="flex items-start gap-4">
            <div class="p-3 bg-white/10 rounded-xl group-hover:bg-white/20 transition-colors text-3xl">
              {{ item.icon }}
            </div>
            <div class="flex-1">
              <h3 class="text-xl font-bold mb-2">{{ item.title }}</h3>
              <p class="text-white/60 leading-relaxed">{{ item.desc }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const approach = [
  { 
    title: 'Understand First', 
    desc: 'Deep dive into requirements and user needs before writing code', 
    icon: '🎯' 
  },
  { 
    title: 'Build Smart', 
    desc: 'Clean, maintainable code with scalability in mind', 
    icon: '💻' 
  },
  { 
    title: 'Deliver Value', 
    desc: 'Focus on business impact and measurable results', 
    icon: '💼' 
  },
  { 
    title: 'Iterate Fast', 
    desc: 'Agile mindset with continuous improvement', 
    icon: '⚡' 
  }
]
</script>
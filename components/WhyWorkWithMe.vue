<!-- Component 3: WhyWorkWithMe.vue -->
<template>
  <section class="relative w-full bg-black text-white border-t border-white/10">
    <!-- LED Header with News Flash -->
    <WhyWorkWithMeHeader />
    
    <div class="max-w-4xl mx-auto px-6 py-20">

      <div class="space-y-6">
        <div
          v-for="(point, idx) in whyHireMe"
          :key="idx"
          class="group flex items-start gap-4 p-6 bg-white/5 border border-white/10 rounded-xl hover:bg-white/10 hover:border-white/20 transition-all duration-300"
        >
          <span class="text-2xl flex-shrink-0 mt-1">✅</span>
          <div>
            <h3 class="text-xl font-semibold mb-2">{{ point.title }}</h3>
            <p class="text-white/60">{{ point.desc }}</p>
          </div>
        </div>
      </div>

      <!-- Extra Assurance Box -->
      <div class="mt-12 p-8 bg-gradient-to-br from-blue-500/10 to-purple-500/10 border border-blue-500/20 rounded-2xl">
        <h3 class="text-2xl font-bold mb-4 text-center">What You Get Instead of Experience</h3>
        <div class="grid md:grid-cols-3 gap-6 mt-6">
          <div class="text-center">
            <div class="text-4xl mb-2">🔥</div>
            <div class="font-semibold mb-1">Hunger</div>
            <div class="text-sm text-white/60">Ready to prove myself and make an impact</div>
          </div>
          <div class="text-center">
            <div class="text-4xl mb-2">🚀</div>
            <div class="font-semibold mb-1">Fresh Perspective</div>
            <div class="text-sm text-white/60">No bad habits, open to learning your way</div>
          </div>
          <div class="text-center">
            <div class="text-4xl mb-2">💪</div>
            <div class="font-semibold mb-1">Dedication</div>
            <div class="text-sm text-white/60">I'll go the extra mile to deliver quality</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const whyHireMe = [
  { 
    title: 'Rapid Learning Curve', 
    desc: 'I adapt quickly to new tech stacks, tools, and team workflows. My self-taught journey proves I can master complex systems independently.' 
  },
  { 
    title: 'Business-Minded Developer', 
    desc: 'I understand that code serves business goals. Every line I write is tied to user value and company objectives, not just technical perfection.' 
  },
  { 
    title: 'Clear Communicator', 
    desc: 'I can explain technical concepts simply for stakeholders and in depth for developers. No jargon when it\'s not needed.' 
  },
  { 
    title: 'Ownership Mentality', 
    desc: 'I take full responsibility for my work from planning to deployment. If something breaks, I fix it. If something can be better, I improve it.' 
  },
  { 
    title: 'Team Player & Eager Learner', 
    desc: 'I thrive in collaborative environments and actively seek mentorship. Your senior devs won\'t need to babysit—I ask smart questions and learn fast.' 
  },
  { 
    title: 'Quality-Obsessed', 
    desc: 'Clean code, testing, and documentation aren\'t optional for me. I build things the right way because I respect my future self and teammates.' 
  }
]
</script>
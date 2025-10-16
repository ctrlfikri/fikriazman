<template>
  <section class="relative overflow-hidden px-6 py-20 lg:py-32">
    <!-- Animated background gradient -->
    <div class="absolute inset-0 bg-gradient-to-r from-blue-600/10 via-purple-600/10 to-pink-600/10 animate-pulse"></div>
    
    <!-- Grid pattern overlay -->
    <div class="absolute inset-0 bg-[linear-gradient(rgba(255,255,255,.05)_1px,transparent_1px),linear-gradient(90deg,rgba(255,255,255,.05)_1px,transparent_1px)] bg-[size:4rem_4rem] [mask-image:radial-gradient(ellipse_80%_50%_at_50%_50%,black,transparent)]"></div>
    
    <div class="relative max-w-6xl mx-auto">
      <div class="flex items-center gap-3 mb-6">
        <div class="h-px flex-1 bg-gradient-to-r from-transparent via-blue-500 to-transparent"></div>
        <span class="text-blue-400 text-sm font-mono tracking-wider">PORTFOLIO</span>
        <div class="h-px flex-1 bg-gradient-to-r from-transparent via-blue-500 to-transparent"></div>
      </div>
      
      <h1 class="text-5xl lg:text-7xl font-bold mb-6 bg-gradient-to-r from-white via-blue-100 to-purple-200 bg-clip-text text-transparent">
        Featured Projects
      </h1>
      
      <p class="text-xl lg:text-2xl text-slate-300 mb-8 max-w-3xl leading-relaxed">
        A curated collection of <span class="text-blue-400 font-semibold">full-stack development</span>, 
        <span class="text-purple-400 font-semibold"> AI/ML solutions</span>, and 
        <span class="text-pink-400 font-semibold"> creative design work</span> — 
        spanning client collaborations and self-driven experiments.
      </p>
      
      <!-- Stats/Skills Grid -->
      <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mt-12">
        <div class="bg-white/5 backdrop-blur-sm border border-white/10 rounded-lg p-4 hover:bg-white/10 transition-all cursor-pointer">
          <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 text-blue-400 mb-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 20l4-16m4 4l4 4-4 4M6 16l-4-4 4-4" />
          </svg>
          <div class="text-2xl font-bold">Full-Stack</div>
          <div class="text-sm text-slate-400">Development</div>
        </div>
        
        <div class="bg-white/5 backdrop-blur-sm border border-white/10 rounded-lg p-4 hover:bg-white/10 transition-all cursor-pointer">
          <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 text-purple-400 mb-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z" />
          </svg>
          <div class="text-2xl font-bold">AI/ML</div>
          <div class="text-sm text-slate-400">Integration</div>
        </div>
        
        <div class="bg-white/5 backdrop-blur-sm border border-white/10 rounded-lg p-4 hover:bg-white/10 transition-all cursor-pointer">
          <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 text-pink-400 mb-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M7 21a4 4 0 01-4-4V5a2 2 0 012-2h4a2 2 0 012 2v12a4 4 0 01-4 4zm0 0h12a2 2 0 002-2v-4a2 2 0 00-2-2h-2.343M11 7.343l1.657-1.657a2 2 0 012.828 0l2.829 2.829a2 2 0 010 2.828l-8.486 8.485M7 17h.01" />
          </svg>
          <div class="text-2xl font-bold">Design</div>
          <div class="text-sm text-slate-400">Graphic & UI/UX</div>
        </div>
        
        <div class="bg-white/5 backdrop-blur-sm border border-white/10 rounded-lg p-4 hover:bg-white/10 transition-all cursor-pointer">
          <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 text-amber-400 mb-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z" />
          </svg>
          <div class="text-2xl font-bold">Creative</div>
          <div class="text-sm text-slate-400">Content</div>
        </div>
      </div>
    </div>
  </section>
</template>
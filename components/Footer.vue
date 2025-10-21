<template>
<section class="relative w-full bg-white text-black border-t border-black/10 py-12 sm:py-24 lg:py-32 overflow-hidden">
  <!-- Animated radial whoosh background -->
  <div class="absolute inset-0 overflow-hidden">
    <div class="absolute inset-0 bg-[radial-gradient(circle_at_center,_rgba(0,0,0,0.05)_0%,_transparent_70%)] animate-zoom"></div>
    <div class="absolute inset-0 bg-[conic-gradient(from_90deg,_rgba(0,0,0,0.03)_0%,_transparent_50%,_rgba(0,0,0,0.03)_100%)] animate-spin-slow opacity-50"></div>
  </div>

  <div class="relative z-10 max-w-4xl mx-auto px-6 lg:px-8 text-center">
    <!-- Small accent line -->
    <div class="w-16 h-[2px] bg-gradient-to-r from-transparent via-black to-transparent mx-auto mb-6"></div>

    <!-- Main heading -->
    <h2 class="text-4xl sm:text-5xl lg:text-6xl font-bold tracking-tight mb-6 bg-gradient-to-r from-black via-gray-800 to-black bg-clip-text text-transparent">
      Let's Make It Official
    </h2>

    <!-- Subtext -->
    <p class="text-gray-600 text-lg sm:text-xl lg:text-2xl max-w-2xl mx-auto mb-12 leading-relaxed">
      Ready to collaborate? Drop me an email or grab my resume to see what we can build together.
    </p>

    <!-- CTA Buttons -->
    <div class="flex flex-col sm:flex-row items-center justify-center gap-4 sm:gap-6">
      <!-- Email Button -->
      <a
        href="mailto:your.email@example.com"
        class="group relative px-8 py-4 bg-black text-white font-semibold rounded-xl overflow-hidden transition-all duration-300 hover:scale-105 hover:shadow-2xl hover:shadow-black/10 w-full sm:w-auto"
      >
        <span class="relative z-10 flex items-center justify-center gap-2">
          <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
              d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z">
            </path>
          </svg>
          Email Me
        </span>
        <div class="absolute inset-0 bg-gradient-to-r from-gray-800 to-black opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
      </a>

      <!-- Resume Button -->
      <a
        href="/resume.pdf"
        download
        class="group relative px-8 py-4 bg-transparent text-black font-semibold rounded-xl border-2 border-black/20 overflow-hidden transition-all duration-300 hover:scale-105 hover:border-black/50 w-full sm:w-auto"
      >
        <span class="relative z-10 flex items-center justify-center gap-2">
          <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
              d="M12 10v6m0 0l-3-3m3 3l3-3m2 8H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z">
            </path>
          </svg>
          Download Resume
        </span>
        <div class="absolute inset-0 bg-black/5 opacity-0 group-hover:opacity-100 transition-opacity duration-300"></div>
      </a>
    </div>

    <!-- Decorative Dots -->
    <div class="mt-16 flex items-center justify-center gap-2">
      <div class="w-2 h-2 rounded-full bg-black/20 animate-pulse"></div>
      <div class="w-2 h-2 rounded-full bg-black/40 animate-pulse" style="animation-delay: 0.2s;"></div>
      <div class="w-2 h-2 rounded-full bg-black/20 animate-pulse" style="animation-delay: 0.4s;"></div>
    </div>

    <!-- Social Links -->
    <div class="mt-8 flex items-center justify-center gap-6">
      <a href="#" class="text-gray-500 hover:text-black transition-colors duration-300">
        <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
          <path
            d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z" />
        </svg>
      </a>
      <a href="#" class="text-gray-500 hover:text-black transition-colors duration-300">
        <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
          <path
            d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z" />
        </svg>
      </a>
    </div>
  </div>
</section>

  <!-- ====== FOOTER ====== -->
<footer class="relative w-full bg-black border-t border-white/10 text-white">
  <div class="max-w-7xl mx-auto px-6 py-16 sm:px-8 lg:px-10">
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-12">

      <!-- Column 1: About / Disclaimer -->
      <div>
        <h3 class="text-lg font-semibold mb-4 text-white">Disclaimer</h3>
        <p class="text-sm text-gray-400 leading-relaxed">
          The contents displayed on this portfolio are for demonstration and personal showcase purposes only. 
          All brand names, visuals, and designs are either original works or recreated as part of design experiments. 
          Please contact me for any usage or collaboration inquiries.
        </p>
      </div>

      <!-- Column 2: Navigation -->
      <div>
        <h3 class="text-lg font-semibold mb-4 text-white">Navigation</h3>
        <ul class="space-y-2 text-gray-400 text-sm">
          <li><NuxtLink to="/" class="hover:text-white transition-colors duration-300">Home</NuxtLink></li>
          <li><NuxtLink to="/about" class="hover:text-white transition-colors duration-300">About</NuxtLink></li>
          <li><NuxtLink to="/projects" class="hover:text-white transition-colors duration-300">Projects</NuxtLink></li>
          <li><NuxtLink to="/contact" class="hover:text-white transition-colors duration-300">Contact</NuxtLink></li>
        </ul>
      </div>

      <!-- Column 3: Social Media -->
      <div>
        <h3 class="text-lg font-semibold mb-4 text-white">Connect</h3>
        <ul class="flex flex-col gap-3 text-gray-400 text-sm">
          <li>
            <a href="https://www.linkedin.com/in/yourprofile" target="_blank" class="flex items-center gap-2 hover:text-white transition">
              <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M19 0h-14C2.239 0 0 2.239 0 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5V5c0-2.761-2.238-5-5-5zm-11 19H5V8h3v11zM6.5 6.268C5.534 6.268 4.75 5.478 4.75 4.5S5.534 2.732 6.5 2.732 8.25 3.522 8.25 4.5 7.466 6.268 6.5 6.268zM20 19h-3v-5.604c0-3.368-4-3.113-4 0V19h-3V8h3v1.765C14.396 7.179 20 6.988 20 12.241V19z"/></svg>
              LinkedIn
            </a>
          </li>
          <li>
            <a href="https://github.com/yourprofile" target="_blank" class="flex items-center gap-2 hover:text-white transition">
              <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0C5.373 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.6.111.793-.261.793-.577v-2.234C5.662 21.303 5.033 19.14 5.033 19.14c-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.565 21.8 24 17.302 24 12 24 5.373 18.627 0 12 0z"/></svg>
              GitHub
            </a>
          </li>
        </ul>
      </div>

      <!-- Column 4: Contact -->
      <div>
        <h3 class="text-lg font-semibold mb-4 text-white">Contact</h3>
        <ul class="space-y-2 text-gray-400 text-sm">
          <li>
            <a href="mailto:ctrlfikri@gmail.com" class="hover:text-white transition-colors duration-300">
              ctrlfikri@gmail.com
            </a>
          </li>
          <li>Seremban, Negeri Sembilan</li>
        </ul>
      </div>
    </div>

    <!-- Divider -->
    <div class="border-t border-white/10 mt-12 pt-6 flex flex-col sm:flex-row justify-between items-center text-gray-500 text-sm">
      <p>© {{ new Date().getFullYear() }} Fikri Azman. All rights reserved.</p>
      <p class="mt-2 sm:mt-0">Powered by <span class="text-white">Nuxt</span> & <span class="text-white">Tailwind</span>. With the help of <span class="text-white">Claude</span>.</p>
    </div>
  </div>

  <div
    class="relative bottom-0 right-0 sm:bottom-4 sm:right-6 text-xs sm:text-sm tracking-[0.25em] font-extrabold text-white/20 select-none
          flex items-end justify-center w-full sm:w-auto pb-2 sm:pb-0"
  >
    FIKRIAZMAN
  </div>

</footer>

</template>

<script setup>
// You can make these props if you want them configurable
</script>

<!-- Custom animations -->
<style>
@keyframes zoom {
  0%, 100% { transform: scale(1); opacity: 0.6; }
  50% { transform: scale(1.2); opacity: 1; }
}
.animate-zoom {
  animation: zoom 8s ease-in-out infinite;
}

@keyframes spin-slow {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
.animate-spin-slow {
  animation: spin-slow 40s linear infinite;
}
</style>
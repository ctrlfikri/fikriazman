<template>
  <nav class="bg-black py-4 px-8">
    <div class="max-w-6xl mx-auto flex justify-between items-center">
      <div class="text-white text-2xl font-extrabold tracking-widest uppercase select-none">
        <span class="inline-block transition-transform duration-300 hover:scale-105">FIKRI</span>
      </div>
      <button
        class="md:hidden text-white focus:outline-none"
        @click="open = !open"
        aria-label="Toggle navigation"
      >
        <svg class="w-7 h-7" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
          <path v-if="!open" stroke-linecap="round" stroke-linejoin="round" d="M4 8h16M4 16h16"/>
          <path v-else stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12"/>
        </svg>
      </button>
      <ul
        class="hidden md:flex space-x-8 text-lg font-semibold tracking-wide"
      >
        <li v-for="item in nav" :key="item.to">
          <NuxtLink
            :to="item.to"
            class="nav-link relative text-white/80 hover:text-white transition"
            active-class="text-white"
          >
            {{ item.label }}
            <span class="nav-underline"></span>
          </NuxtLink>
        </li>
      </ul>
    </div>
    <!-- Mobile menu -->
    <transition name="fade">
      <ul
        v-if="open"
        class="md:hidden flex flex-col items-end mt-4 space-y-2 text-lg font-semibold tracking-wide"
      >
        <li v-for="item in nav" :key="item.to">
          <NuxtLink
            :to="item.to"
            class="nav-link relative text-white/80 hover:text-white transition"
            active-class="text-white"
            @click="open = false"
          >
            {{ item.label }}
            <span class="nav-underline"></span>
          </NuxtLink>
        </li>
      </ul>
    </transition>
  </nav>
</template>

<script setup>
import { ref } from 'vue'
const open = ref(false)
const nav = [
  { to: '/', label: 'Home' },
  { to: '/about', label: 'About' },
  { to: '/projects', label: 'Projects' },
  { to: '/contact', label: 'Contact' }
]
</script>

<style scoped>
.nav-link {
  padding-bottom: 2px;
  letter-spacing: 0.08em;
  display: inline-block;
}
.nav-underline {
  display: block;
  height: 2px;
  width: 100%;
  background: linear-gradient(90deg, #fff 60%, transparent 100%);
  position: absolute;
  left: 0;
  bottom: -2px;
  opacity: 0;
  transform: scaleX(0.6);
  transition: opacity 0.2s, transform 0.3s;
}
.nav-link:hover .nav-underline,
.nav-link:focus .nav-underline,
.router-link-exact-active .nav-underline {
  opacity: 1;
  transform: scaleX(1);
}
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.2s;
}
.fade-enter-from, .fade-leave-to {
  opacity: 0;
}
</style>
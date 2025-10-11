<template>
  <footer class="bg-black text-white py-8">
    <div class="flex flex-col items-center gap-4">
      
      <!-- Copyright -->
      <p class="text-sm text-white/70">&copy; {{ new Date().getFullYear() }} Fikri Azman. All rights reserved.</p>
      
      <!-- Navigation Links -->
      <div class="flex gap-6">
        <a href="/about" class="footer-link">About</a>
        <a href="/projects" class="footer-link">Projects</a>
        <a href="/contact" class="footer-link">Contact</a>
      </div>

      <!-- Social Icons -->
      <div class="flex gap-4 mt-2">
        <div class="w-6 h-6 bg-white/20 rounded-full flex items-center justify-center hover:bg-white/50 transition">
          🌐
        </div>
        <div class="w-6 h-6 bg-white/20 rounded-full flex items-center justify-center hover:bg-white/50 transition">
          🐦
        </div>
        <div class="w-6 h-6 bg-white/20 rounded-full flex items-center justify-center hover:bg-white/50 transition">
          💼
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
// No JS needed for now
</script>

<style scoped>
.footer-link {
  position: relative;
  font-weight: 600;
  color: #ffffffcc;
  transition: all 0.3s ease;
}

.footer-link::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -2px;
  width: 0%;
  height: 2px;
  background: linear-gradient(90deg, #ffe600, #ffb7c5, #00ffcc, #ff00ff);
  border-radius: 2px;
  transition: width 0.3s ease;
}

.footer-link:hover {
  color: white;
}

.footer-link:hover::after {
  width: 100%;
}

/* Subtle glow for the entire footer text */
footer p,
footer a {
  text-shadow: 0 0 6px rgba(255, 255, 255, 0.2);
}
</style>

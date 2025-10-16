<template>
  <section class="min-h-screen bg-black text-white px-6 py-24 flex flex-col items-center justify-center relative overflow-hidden">
    <!-- Background Gradient Glow -->
    <div class="absolute inset-0 bg-gradient-to-b from-transparent via-white/5 to-transparent blur-3xl opacity-40"></div>

    <!-- Heading -->
    <div class="relative text-center mb-16 z-10">
      <h1 class="text-5xl sm:text-6xl font-bold mb-4 bg-gradient-to-r from-white via-gray-300 to-gray-600 bg-clip-text text-transparent">
        Let’s Build Something Great
      </h1>
      <p class="text-white/60 text-lg max-w-2xl mx-auto">
        Whether you have a project in mind, want to collaborate, or just want to say hi — I’d love to hear from you.
      </p>
    </div>

    <!-- Contact Form -->
    <form
      @submit.prevent="handleSubmit"
      class="relative w-full max-w-xl bg-white/5 backdrop-blur-md border border-white/10 rounded-2xl p-8 space-y-6 z-10"
    >
      <div>
        <label class="block text-sm text-white/70 mb-2">Name</label>
        <input
          v-model="form.name"
          type="text"
          required
          class="w-full bg-transparent border border-white/20 rounded-lg p-3 focus:border-white/50 focus:outline-none"
          placeholder="Your name"
        />
      </div>

      <div>
        <label class="block text-sm text-white/70 mb-2">Email</label>
        <input
          v-model="form.email"
          type="email"
          required
          class="w-full bg-transparent border border-white/20 rounded-lg p-3 focus:border-white/50 focus:outline-none"
          placeholder="your@email.com"
        />
      </div>

      <div>
        <label class="block text-sm text-white/70 mb-2">Message</label>
        <textarea
          v-model="form.message"
          rows="5"
          required
          class="w-full bg-transparent border border-white/20 rounded-lg p-3 focus:border-white/50 focus:outline-none resize-none"
          placeholder="Tell me about your idea..."
        ></textarea>
      </div>

      <button
        type="submit"
        class="w-full py-3 rounded-lg bg-gradient-to-r from-white to-gray-400 text-black font-semibold hover:scale-[1.02] transition-transform duration-200"
      >
        Send Message
      </button>
    </form>

    <!-- Social Links -->
    <div class="relative flex items-center justify-center gap-6 mt-12 z-10">
      <a href="mailto:fikriazmanofficial@gmail.com" class="text-white/60 hover:text-white transition">Email</a>
      <a href="https://github.com/fikriazman" target="_blank" class="text-white/60 hover:text-white transition">GitHub</a>
      <a href="https://linkedin.com/in/fikriazman" target="_blank" class="text-white/60 hover:text-white transition">LinkedIn</a>
      <a href="https://dribbble.com/fikriazman" target="_blank" class="text-white/60 hover:text-white transition">Dribbble</a>
    </div>

    <!-- Floating Accent Circles -->
    <div class="absolute top-20 left-10 w-72 h-72 bg-white/10 rounded-full blur-3xl animate-pulse"></div>
    <div class="absolute bottom-10 right-10 w-80 h-80 bg-white/5 rounded-full blur-3xl animate-pulse"></div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const form = ref({
  name: '',
  email: '',
  message: ''
})

const handleSubmit = () => {
  console.log('Form submitted:', form.value)
  alert('Thanks for reaching out, I’ll get back to you soon!')
  form.value = { name: '', email: '', message: '' }
}
</script>

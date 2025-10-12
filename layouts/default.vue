<template>
  <div>
    <Navbar />
    <NuxtPage />
    <Footer />
  </div>
</template>

<script setup>
useHead({
  title: "Fikri Azman — Portfolio",
  meta: [
    { name: "description", content: "Portfolio of Fikri Azman, Web Developer & Designer" },
  ],
  link: [
    { rel: "icon", type: "image/x-icon", href: "/favicon.ico" },
  ],
})
</script>

<style scoped>
</style>

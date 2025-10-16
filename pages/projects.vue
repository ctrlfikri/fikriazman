<template>
  <main class="min-h-screen bg-black text-white">
    <!-- About Hero -->
    <div class="border border-white/10 w-full max-w-7xl mx-auto">
      <OfficialProjects />
    </div>

        <!-- About Hero -->
      <div class="border border-white/10 w-full max-w-7xl mx-auto">
      <SelfWorks />
    </div>
  </main>
</template>

<script setup>
import OfficialProjects from "@/components/OfficialProjects.vue"
import SelfWorks from "@/components/SelfWorks.vue";
</script>
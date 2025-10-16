<!-- pages/projects.vue -->
<template>
  <main class="min-h-screen bg-black text-white">
    <!-- Hero Section -->
     <div class="border border-white/10 w-full max-w-7xl mx-auto">
          <ProjectsHero />
     </div>


    <!-- Official Projects Section -->
    <div class="border border-white/10 w-full max-w-7xl mx-auto">
      <ProjectSectionHeader 
        title="Official Projects"
        description="Professional work and client collaborations — delivering end-to-end solutions from concept to deployment."
        icon="briefcase"
        gradient="from-blue-500 to-purple-500"
      />
      <div class="border border-white/10 w-full max-w-7xl mx-auto">
        <OfficialProjects />
      </div>
    </div>

    <!-- Self-Work Projects Section -->
    <div class="border border-white/10 w-full max-w-7xl mx-auto">
      <ProjectSectionHeader 
        title="Passion Projects"
        description="Self-driven experiments and creative explorations — where curiosity meets innovation. Building to learn, learning to build."
        icon="sparkles"
        gradient="from-purple-500 to-pink-500"
      />
      <div class="border border-white/10 w-full max-w-7xl mx-auto">
        <SelfWorks />
      </div>
    </div>
  </main>
</template>

<script setup>
import OfficialProjects from "@/components/OfficialProjects.vue"
import SelfWorks from "@/components/SelfWorks.vue"
import ProjectsHero from "@/components/ProjectsHero.vue"
import ProjectSectionHeader from "@/components/ProjectSectionHeader.vue"
</script>

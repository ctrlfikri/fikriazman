<template>
  <div class="flex flex-col bg-black">
    <!-- Hero -->
    <div class="w-full bg-black">
      <div class="border border-white/10 w-full max-w-7xl mx-auto">
        <HeroSection />
      </div>
    </div>

    <!-- Skills -->
    <div class="w-full bg-black">
      <div class="max-w-7xl mx-auto">
        <div class="flex flex-col lg:flex-row items-stretch w-full">
          <SkillsSectionHeader />
          <div class="lg:w-2/3 border border-white/10 overflow-visible">
            <SkillCard />
          </div>
        </div>
      </div>
    </div>

    <!-- Projects Banner -->
    <div class="w-full bg-black">
      <div class="max-w-7xl mx-auto">
        <ProjectsBanner />
      </div>
    </div>

    <!-- Projects -->
    <div class="w-full bg-black">
      <div class="max-w-7xl mx-auto">
        <ProjectCard />
      </div>
    </div>

    <!-- Work Experience -->
    <div class="w-full bg-black">
      <div class="border border-white/10 w-full max-w-7xl mx-auto">
        <WorkExperience />
      </div>
    </div>

    <!-- Data -->
    <div class="w-full bg-black">
      <div class="border border-white/10 w-full max-w-7xl mx-auto">
        <DataCard />
      </div>
    </div>

    <!-- About Me -->
    <div class="w-full bg-black">
      <div class="border border-white/10 w-full max-w-7xl mx-auto">
        <AboutMe />
      </div>
    </div>

    <!-- Tech Stack -->
    <div class="w-full bg-black">
      <div class="max-w-7xl mx-auto">
        <TechStackBanner />
      </div>
    </div>

    <!-- Roles -->
    <div class="w-full bg-black">
      <div class="border border-white/10 w-full max-w-7xl mx-auto">
        <RoleCard />
      </div>
    </div>
  </div>
</template>

<script setup>
import HeroSection from '@/components/HeroSection.vue'
import SkillsSectionHeader from '@/components/SkillSectionHeader.vue'
import SkillCard from '@/components/SkillCard.vue'
import ProjectsBanner from '@/components/ProjectBanner.vue'
import ProjectCard from '@/components/ProjectCard.vue'
import WorkExperience from '@/components/WorkExperience.vue'
import DataCard from '@/components/DataCard.vue'
import AboutMe from '@/components/AboutMe.vue'
import RoleCard from '@/components/RoleCard.vue'
import TechStackBanner from '@/components/TechStackBanner.vue'
</script>
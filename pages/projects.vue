<template>
  <div class="container mx-auto py-10">
    <h1 class="text-3xl font-bold mb-6">Projects</h1>
    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <ProjectCard
        v-for="project in projects"
        :key="project.id"
        :title="project.title"
        :description="project.description"
        :link="project.link"
      />
    </div>
  </div>
</template>

<script setup>
import ProjectCard from '@/components/ProjectCard.vue'

const projects = [
  {
    id: 1,
    title: 'Project One',
    description: 'Description for project one.',
    link: 'https://example.com/project-one'
  },
  {
    id: 2,
    title: 'Project Two',
    description: 'Description for project two.',
    link: 'https://example.com/project-two'
  },
  {
    id: 3,
    title: 'Project Three',
    description: 'Description for project three.',
    link: 'https://example.com/project-three'
  }
]
</script>

<style scoped>
.container {
  max-width: 1200px;
}
</style>
<script setup>
  import projectData from '@/assets/projects.json'
</script>

<template>
  <div>
    <div class="flex flex-col items-center h-screen">
      <h1 class="text-7xl py-15">My Projects</h1>
      <div v-for="(project, index) in projectData" :key="index">
        <div class="py-3">
          <ProjectCard :title="project.title" :desc="project.desc" />
        </div>
      </div>
    </div>
  </div>
</template>

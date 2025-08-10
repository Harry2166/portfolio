<script setup>
  import projectData from '@/assets/projects.json'
</script>
<template>
  <div>
    <div class="flex flex-col items-center h-screen">
      <h1 class="text-7xl py-15">My Projects</h1>
      <div v-for="(project, index) in projectData" :key="index">
        <div class="group py-3 relative">
          <div v-if="index % 2 === 0" class="flex flex-row justify-center">
            <ProjectCard :title="project.title" :desc="project.desc" />
            <div class="px-5 absolute left-full top-1/2 transform -translate-y-1/2 ml-3 opacity-0 group-hover:opacity-100 transition-opacity duration-200 pointer-events-none group-hover:pointer-events-auto">
              <ProjectSummary :summary="project.summary"/>
            </div>
          </div>
          <div v-else class="flex flex-row justify-center">
            <div class="px-5 absolute right-full top-1/2 transform -translate-y-1/2 mr-3 opacity-0 group-hover:opacity-100 transition-opacity duration-200 pointer-events-none group-hover:pointer-events-auto">
              <ProjectSummary :summary="project.summary"/>
            </div>
            <ProjectCard :title="project.title" :desc="project.desc" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

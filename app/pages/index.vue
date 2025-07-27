<template>
  <div style="background-color: var(--bg); color: var(--text)">
    <div
      v-for="(slide, index) in slides"
      :key="index"
      ref="slideRefs"
      class="h-screen relative"
    >
      <div
        class="sticky top-0 h-screen flex flex-col items-center justify-center transition-opacity duration-700"
        :class="{ 'opacity-100': activeSlide === index, 'opacity-0': activeSlide !== index }"
      >
        <h2 v-if="slide.centered" class="text-5xl lg:text-9xl md:text-7xl py-5">{{ slide.title }}</h2>
        <h2 v-else class="text-5xl py-5">{{slide.title}}</h2>
        <p class="mt-2 text-2xl">{{ slide.subtitle }}</p>
        <div v-if="slide.final_slide" class="flex flex-row items-center px-5">
          <h1 class="px-5">Python</h1>
          <h1 class="px-5">Typescript</h1>
          <h1 class="px-5">HTML</h1>
          <h1 class="px-5">CSS</h1>
          <h1 class="px-5">Tailwind</h1>
          <h1 class="px-5">Django</h1>
          <h1 class="px-5">PostgreSQL</h1>
          <h1 class="px-5">FastAPI</h1>
          <h1 class="px-5">Vue</h1>
          <h1 class="px-5">Svelte</h1>
          <h1 class="px-5">Godot</h1>
          <h1 class="px-5">Unity</h1>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, nextTick } from 'vue';

const slides = ref([
  { title: "Hi I'm Harry.", subtitle: 'Fullstack Developer, Game Developer, Lifelong Learner', centered: true, final_slide: false },
  { title: "I am a Computer Science Enthusiast.", subtitle: 'I am interested in all things Computer Science and I am currently pursuing a Computer Science degree in University of the Philippines Diliman.', centered: false, final_slide: false },
  { title: "I am an aspiring full stack developer, specializing in the backend.", subtitle: 'I can dabble in some frontend though!', centered: false, final_slide: false },
  { title: "I am also an aspiring game developer, specializing in programming.", subtitle: 'I got interested in Computer Science because of video games!', centered: false, final_slide: false },
  { title: "Here is my skillset", subtitle: 'I will get the icons for these later', centered: false, final_slide: true },
]);

const slideRefs = ref([]);
const activeSlide = ref(0);
let observer;

onMounted(async () => {
  await nextTick(); 

  observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          const index = slideRefs.value.findIndex((el) => el === entry.target);
          if (index !== -1) {
            activeSlide.value = index;
          }
        }
      });
    },
    {
      threshold: 0.6,
    }
  );

  slideRefs.value.forEach((el) => {
    if (el) observer.observe(el);
  });
});

onUnmounted(() => {
  if (observer) observer.disconnect();
});
</script>

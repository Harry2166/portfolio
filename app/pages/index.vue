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
        <h2 v-else class="text-3xl lg:text-6xl md:text-5xl py-5">{{ slide.title }}</h2>
        <p class="text-xl lg:text-3xl md:text-2xl py-5">{{ slide.subtitle }}</p>
        <div v-if="slide.final_slide" class="flex flex-row items-center px-5">
          <Icon name="icon:python" class="px-6 text-3xl sm:text-4xl md:text-5xl lg:text-6xl sm:px-7 md:px-8 lg:px-10" />
          <Icon name="icon:typescript" class="px-6 text-3xl sm:text-4xl md:text-5xl lg:text-6xl sm:px-7 md:px-8 lg:px-10" />
          <Icon name="icon:vue" class="px-6 text-3xl sm:text-4xl md:text-5xl lg:text-6xl sm:px-7 md:px-8 lg:px-10" />
          <Icon name="icon:svelte" class="px-6 text-3xl sm:text-4xl md:text-5xl lg:text-6xl sm:px-7 md:px-8 lg:px-10" />
          <Icon name="icon:tailwind" class="px-6 text-3xl sm:text-4xl md:text-5xl lg:text-6xl sm:px-7 md:px-8 lg:px-10" />
          <Icon name="icon:django" class="px-6 text-3xl sm:text-4xl md:text-5xl lg:text-6xl sm:px-7 md:px-8 lg:px-10" />
          <Icon name="icon:fastapi" class="px-6 text-3xl sm:text-4xl md:text-5xl lg:text-6xl sm:px-7 md:px-8 lg:px-10" />
          <Icon name="icon:godot" class="px-6 text-3xl sm:text-4xl md:text-5xl lg:text-6xl sm:px-7 md:px-8 lg:px-10" />
          <Icon name="icon:unity" class="px-6 text-3xl sm:text-4xl md:text-5xl lg:text-6xl sm:px-7 md:px-8 lg:px-10" />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, nextTick } from 'vue';

const slides = ref([
  { title: "Hi I'm Harry.", subtitle: 'Fullstack Developer, Game Developer, Lifelong Learner', centered: true, final_slide: false },
  { title: "I am a Computer Science Enthusiast.", subtitle: 'I am currently pursuing a Computer Science degree', centered: false, final_slide: false },
  { title: "I specialize in backend development", subtitle: 'I can dabble in some frontend though!', centered: false, final_slide: false },
  { title: "I'm also an aspiring game developer.", subtitle: 'I got interested in Computer Science because of video games!', centered: false, final_slide: false },
  { title: "Here is my skillset", subtitle: '', centered: false, final_slide: true },
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

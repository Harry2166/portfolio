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
        <h2 v-if="slide.centered" class="text-9xl">{{ slide.title }}</h2>
        <h2 v-else class="text-5xl font-bold">{{slide.title}}</h2>
        <p class="mt-2">{{ slide.subtitle }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted, nextTick } from 'vue';

const slides = ref([
  { title: "Hi I'm Harry.", subtitle: '', centered: true},
  { title: "I am going to test this slide", subtitle: '', centered: false},
]);

const slideRefs = ref([]);
const activeSlide = ref(0);
let observer;

onMounted(async () => {
  await nextTick(); // Wait for DOM updates

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

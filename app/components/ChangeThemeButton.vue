<script setup>
  import { ref } from 'vue'
  const colorMode = ref(false) // true -> light mode, false -> dark mode
  const toggleTheme = () => {
    colorMode.value = !colorMode.value
    document.body.classList.toggle('light', colorMode.value)
  }
</script>

<template>
  <div class="px-5">
    <button @click="toggleTheme" class="p-2 border theme-button">
      <Icon v-if="!colorMode" name="mdi:white-balance-sunny" class="scale-110"/>
      <Icon v-else name="material-symbols:dark-mode" class="scale-110"/>
    </button>
  </div>
</template>

<style scoped>
.theme-button {
  background-color: var(--bg-light);
  color: var(--text);
  transition: background-color 0.2s ease;
}

.theme-button:hover {
  background-color: var(--bg-dark);
}
</style>

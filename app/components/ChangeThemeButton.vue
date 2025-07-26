<script setup>
const toggleTheme = () => {
  document.body.classList.toggle('light')
}
</script>

<template>
  <div class="px-5 py-5">
    <button @click="toggleTheme" class="p-2 border theme-button">Toggle Theme</button>
  </div>
</template>

<style scoped>
.theme-button {
  background-color: var(--bg-light);
  color: var(--text);
  transition: background-color 0.2s ease;
}

.theme-button:hover {
  background-color: var(--bg-light);
}
</style>

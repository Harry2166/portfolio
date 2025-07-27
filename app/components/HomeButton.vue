<template>
  <div class="px-5 py-5">
    <NuxtLink to="/" class="p-2 border theme-button">
      <Icon name="material-symbols:home" class="scale-110"/>
    </NuxtLink>
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

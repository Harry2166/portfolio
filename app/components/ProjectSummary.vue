<script setup>
defineProps({
	summary: {
		type: String,
		default: "insert something here"
	},
})

</script>

<template>
  <div class="w-80 max-w-sm px-5 py-3" style="background-color: var(--bg-light);"> 
    <h1 class="flex flex-col items-center">{{summary}}</h1>
  </div>
</template>

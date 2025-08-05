<script setup>
defineProps({
	title: {
		type: String,
		default: "insert something here"
	}
})

</script>

<template>
  <div class="w-full hover:scale-110" style="background-color: var(--bg-light);"> 
    <h1>{{title}}</h1>
  </div>
</template>

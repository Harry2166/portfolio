<script setup>
defineProps({
	title: {
		type: String,
		default: "insert something here"
	},
  desc: {
    type: String,
    default: "insert something here"
  }
})

</script>

<template>
  <div class="w-full hover:scale-110 px-5 py-3" style="background-color: var(--bg-light);"> 
    <h1 class="flex flex-col items-center">{{title}}</h1>
  </div>
</template>

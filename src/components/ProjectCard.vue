<template>
	<div class="col-md-3 m-1 p-2 	">
		<a
		  v-if="project.link"
		  :href="project.link"
		  target="_blank"
		  rel="noopener noreferrer"
		  class="text-decoration-none text-dark"
		>
		  <div class="card h-100 shadow-sm p-3 rounded-3 project-card hoverable">
		    <img :src="project.image" class="card-img-top card-img" alt="..." />
		    <div class="card-body">
		      <h5 class="card-title">{{ project.title }}</h5>
		      <p class="card-text">{{ project.description }}</p>
		    </div>
		  </div>
		</a>

		<div
		  v-else
		  class="card h-100 shadow-sm p-3 rounded-3 project-card"
		>
		  <img :src="project.image" class="card-img-top card-img" alt="..." />
		  <div class="card-body">
		    <h5 class="card-title">{{ project.title }}</h5>
		    <p class="card-text">{{ project.description }}</p>
		  </div>
		</div>
	</div>
</template>

<script setup>
import { computed } from 'vue'
// import { defineProps } from 'vue';

const props = defineProps({
	project: Object
})

const hasWebsite = computed(() => !!props.project.link);
</script>

<style scoped>
.project-card {
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.hoverable:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
}
.card-img {
  height: 200px;
  object-fit: cover;
  border-radius: 10px;
}
</style>
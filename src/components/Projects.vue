<template>
	<section class="pt-5" id="projects">
		<div class="container">
			<h1 class="mt-5 text-center">My Projects</h1>

		<div
			v-for="(group, index) in chunkedProjects"
			:key="index"
			class="row justify-content-center"
			>

			<ProjectCard
			v-for="project in group"
			:key="project.id"
			:project="project"
			/>
		</div>
		</div>
		
    </section>
</template>

<script setup>
	import { computed } from 'vue';
	import ProjectCard from './ProjectCard.vue';
	import projects from '../data/projects.json';

	const chunkSize = 3

	const chunkedProjects = computed(() => {
		const chunks = [];
		for (let i = 0; i < projects.length; i += chunkSize) {
			chunks.push(projects.slice(i, i + chunkSize))
		}
		return chunks;
	})
</script>

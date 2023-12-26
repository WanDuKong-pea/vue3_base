<template>
	<div>
		<div>
			<h1>original</h1>
			<p>subscribers: {{ subscribers }}</p>
			<p>views: {{ views }}</p>
			<p>likes: {{ likes }}</p>
		</div>
		<hr />
		<div v-once>
			<h1>v-once</h1>
			<p>subscribers: {{ subscribers }}</p>
			<p>views: {{ views }}</p>
			<p>likes: {{ likes }}</p>
		</div>
		<hr />
		<div v-memo="[views]">
			<h1>v-memo</h1>
			<p>subscribers: {{ subscribers }}</p>
			<p>views: {{ views }}</p>
			<p>likes: {{ likes }}</p>
		</div>
		<button @click="subscribers++">subscribers++</button>
		<button @click="views++">views++</button>
		<button @click="likes++">likes++</button>
	</div>
</template>

<script>
import { ref } from 'vue';
export default {
	setup() {
		const subscribers = ref(4000);
		const views = ref(400);
		const likes = ref(200);
		return {
			subscribers,
			views,
			likes,
		};
	},
};
</script>

<style></style>

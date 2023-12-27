<template>
	<div>
		<h2>input Value</h2>
		<h4>단방향 바인딩 v-bind</h4>
		<input type="text" :value="inputValue1" />
		<div>{{ inputValue1 }}</div>
		<h4>양방향 바인딩 v-on:input</h4>
		<!-- <input type="text" v-on:input="event => (inputValue1 => event.target.value)"/> -->
		<input
			type="text"
			:value="inputValue2"
			@input="event => (inputValue2 = event.target.value)"
		/>
		<div>{{ inputValue2 }}</div>
		<h4>양방향 바인딩 v-model</h4>
		<input type="text" v-model="inputValue3" />
		<div>{{ inputValue3 }}</div>

		<hr />
		<h2>Textarea Value</h2>
		<h4>단방향 바인딩 v-bind</h4>
		<textarea :value="textareaValue1"></textarea>
		<div>{{ textareaValue1 }}</div>
		<h4>양방향 바인딩 :value, @input</h4>
		<textarea
			:value="textareaValue2"
			@input="event => (textareaValue2 = event.target.value)"
		></textarea>
		<div>{{ textareaValue2 }}</div>
		<h4>양방향 바인딩 v-model</h4>
		<textarea v-model="textareaValue3"></textarea>
		<div>{{ textareaValue3 }}</div>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const inputValue1 = ref('hello1');
		const inputValue2 = ref('hello2');
		const inputValue3 = ref('hello3');
		const textareaValue1 = ref('textarea1');
		const textareaValue2 = ref('textarea2');
		const textareaValue3 = ref('textarea3');
		return {
			inputValue1,
			inputValue2,
			inputValue3,
			textareaValue1,
			textareaValue2,
			textareaValue3,
		};
	},
};
</script>

<style></style>

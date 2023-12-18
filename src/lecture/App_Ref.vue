<!-- 
	ref()의 동작 원리를 reactive({})로 이해하기 
	ref()함수는 number, string, boolean, object, array 등을 reactive()로 감싸서 반환한다.
-->

<template>
	<div>
		<p>{{ message.value }}</p>
		<button v-on:click="addMessage">add Click</button>
		<!-- v-on:click의 단축문법 >> @Click -->

		<p>{{ refMessage }}</p>
		<button v-on:click="addRefMessage">add Click</button>
	</div>
</template>

<script>
import { reactive, ref } from 'vue';
export default {
	setup() {
		const message = reactive({
			value: 'Hello Vue!',
		});

		const addMessage = () => {
			message.value = message.value + '!';
		};

		const refMessage = ref('Hello Vue!');
		const addRefMessage = () => {
			refMessage.value = refMessage.value + '!';
		};

		return {
			message,
			addMessage,
			refMessage,
			addRefMessage,
		};
	},
};
</script>

<style lang="scss" scoped></style>

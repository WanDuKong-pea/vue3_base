<template>
	<div>
		<button @click="printEventInfo('Hello Vue3', $event)">
			inline event handelr
		</button>
		<hr />
		<input type="text" @keyup="onKeyupHandler($event)" />
	</div>
</template>

<script>
export default {
	setup() {
		const printEventInfo = (message, event) => {
			console.log('message: ', message);
			console.log('event: ', event);
			console.log('event.target: ', event.target);
			console.log('event.target.tagName: ', event.target.tagName);
		};

		const onKeyupHandler = event => {
			console.log('event.key: ', event.key);
			console.log('event.target.value: ', event.target.value);
		};
		return {
			printEventInfo,
			onKeyupHandler,
		};
	},
};
</script>

<style></style>

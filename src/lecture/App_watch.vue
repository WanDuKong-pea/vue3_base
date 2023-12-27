<template>
	<div></div>
</template>

<script>
import { ref, watch } from 'vue';
export default {
	setup() {
		const message = ref('');

		watch(message, (newValue, oldValue) => {
			//사용 가능 영역
			//DOM 변경
			//API 호출
			//또다른 반응형 상태 변경

			console.log('newValue: ', newValue);
			console.log('oldValue: ', oldValue);
		});
		return {
			message,
		};
	},
};
</script>

<style></style>

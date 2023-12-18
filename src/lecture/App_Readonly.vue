<!--
	readonly 로 반응형이나, 수정이 불가능한 데이터를 만들어보자
-->
<template>
	<div></div>
</template>

<script>
import { reactive, readonly } from 'vue';
export default {
	setup() {
		const original = reactive({
			count: 0,
		});

		original.count++;
		console.log(original.count); // 1

		//readonly(반응형 데이터)
		//기존 반응형 데이터를 그대로 복사해 반응형 데이터를 연결해주지만, 수정이 불가능하다.
		//기존 반응형 데이터를 변경하면 변경값이 반영됨.
		const copy = readonly(original);
		copy.count++;
		console.log(copy.count); // 1

		original.count++;
		console.log(copy.count); // 2
		return {};
	},
};
</script>

<style lang="scss" scoped></style>

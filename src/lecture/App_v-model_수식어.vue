<template>
	<div>
		<!--
			.lazy 수식어를 사용하면 change 이벤트 이후 동기화가 됨 
			//포커스가 input에서 벗어났을때 동기화
		-->
		<input type="text" v-model.lazy="inputValue" />
		{{ inputValue }}
		<!--
			사용자 입력이 자동으로 number 타입으로 형변환 되기를 원하면 .number 수식어를 사용
			문자 입력 안됨
		-->
		<input type="number" v-model.number="inputValue2" />
		{{ inputValue2 }}
		<!--
			사용자가 입력한 내용에서 자동으로 앞뒤 공백이 제거되길 원하면 .trim 수식어를 사용
		-->
		<input type="text" v-model.trim="inputValue3" />
		[{{ inputValue3 }}]
	</div>
</template>

<script>
import { ref } from 'vue';
export default {
	setup() {
		const inputValue = ref('');
		const inputValue2 = ref(0);
		const inputValue3 = ref('');
		return {
			inputValue,
			inputValue2,
			inputValue3,
		};
	},
};
</script>

<style></style>

<template>
	<div></div>
</template>

<script>
import { ref, watch } from 'vue';
export default {
	setup() {
		const message = ref('Hello Vue 3!');
		const reverseMessage = ref('');

		//최초 렌더링 시점에도 실행되도록 immediate 옵션을 true로 설정
		// watch(
		// 	message,
		// 	() => {
		// 		reverseMessage.value = message.value.split('').reverse().join('');
		// 		console.log(message.value, reverseMessage.value);
		// 	},
		// 	{ immediate: true },
		// );

		//아래 코드와 위 코드 같음
		//immediate:true를 꼭 쓰지 않아도 됨
		const reverseFunc = newMessage => {
			reverseMessage.value = newMessage.split('').reverse().join('');
			console.log(message.value, reverseMessage.value);
		};
		watch(message, reverseFunc);
		reverseFunc(message.value);

		//watch vs computed
		//computed는 의존하는 데이터가 변경될 때 사용
		//위와 같이 message가 변경될 때 reverseMessage가 변경되어지는 종속관계라면 computed를 사용하는 것이 좋음
		//computed는 캐싱을 하기 때문에 성능상 이점이 있음
		//watch는 데이터가 변경될 때마다 실행되기 때문에 성능상 이점이 없음
		//watch는 인스턴스의 상태(ref, reactive 변수)의 변경 시점에 특정 액션(call api, push, pop 등)을 수행하고 싶을 때 사용
		//watch는 비동기 처리가 가능하고 computed는 불가능
		//대게의 경우 computed를 사용하고, watch는 특정 데이터의 변경 시점에 비동기 처리를 해야 할 때 사용

		return { message, reverseMessage };
	},
};
</script>

<style></style>

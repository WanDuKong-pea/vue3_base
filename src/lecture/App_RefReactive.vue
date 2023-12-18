<!--
	ref 함수를 reative 객체의 속성으로 정의하면 어떻게 해야할까?
	보다 일반적으로 Vue 3에서는 ref와 reactive를 혼합해서 사용하는 것보다 
	ref와 reactive를 구분하여 값을 관리하는 것이 더 권장됨
-->
<template>
	<div>
		<p>{{ state.count }}</p>
		<button @click="refIncrement">refIncrement</button>
		<button @click="reactiveIncrement">reactiveIncrement</button>
		<button @click="reactiveIncrement2">reactiveIncrement2</button>
		<hr />
		<p>{{ arr[0].value }}</p>
		<!--
			불가능 코드 <p>{{ arr[0].message }}</p> 
			이유: arr[0]은 ref이므로 value를 사용해야함
			arr[0]에서 인덱스 0이 message(ref)를 지칭하는 것과 같음
		-->
		<button @click="arrRefIncrement">arrRefIncrement</button>
		<button @click="arrReactiveIncrement">arrReactiveIncrement</button>
	</div>
</template>

<script>
import { reactive, ref } from 'vue';
export default {
	setup() {
		//ref -> Object
		const count = ref(0);
		const state = reactive({
			count,
		});
		const refIncrement = () => {
			count.value++;
		};
		const reactiveIncrement = () => {
			state.count++;
		};

		const reactiveIncrement2 = () => {
			// ref는 값을 반응형으로 만들어주고, reactive는 객체 전체를 반응형으로 만들어줌
			// state.count는 ref로 만들어진 값이므로, count.value로 접근해야함
			// 아래 코드에 오류가 발생하는 이유는 state.count가 이미 ref이므로 해당 속성에 직접적으로 value를
			// 할당하면 안되기 때문임.
			// 따라서 state.count.value++가 아닌 state.count++로 접근해야함
			state.count.value++;
		};

		//ref -> Array
		const message = ref('Hello');
		const arr = reactive([message]);
		const arrRefIncrement = () => {
			message.value += '!';
		};
		const arrReactiveIncrement = () => {
			arr[0].value += '!';
		};
		return {
			count,
			state,
			refIncrement,
			reactiveIncrement,
			reactiveIncrement2,

			message,
			arr,
			arrRefIncrement,
			arrReactiveIncrement,
		};
	},
};
</script>

<styled></styled>

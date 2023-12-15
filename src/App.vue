<template>
	<div>
		<p>{{ counter }}</p>
		<button @click="increment">click!</button>
		<p>{{ message }}</p>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	//setup 함수에서 변수를 선언하고, return으로 변수를 내보내면, template에서 사용할 수 있다.
	setup() {
		//setup 함수의 첫번째 인자는 props이다. 이 props는 반응형 객체이다.
		//props 객체를 구조 분해 할당을 하면 반응성을 잃는데 따라서 항상 props.xxx 형식으로 props에 액세스하는 것이 좋다.
		//ex) const { name } = props; // 이렇게 하면 반응성을 잃는다.
		//ex) const name = props.name; // 이렇게 하면 반응성을 유지한다.

		//setup 함수의 두번째 인자는 context이다.
		//context는 컴포넌트의 모든 속성을 포함하는 객체이다.
		//context는 반응형이 아니기 때문에 구조 분해 할당을 해도 반응성을 잃지 않는다.

		//뒤에서 setup 함수의 인자에 대해 더 자세히 다룬다.
		//이번 시간에는 setup 함수의 인자로 첫번째 인자인 props, 두번째 인자인 context에 대해서만 인지하자.

		const counter = ref(0);
		const increment = () => {
			counter.value++;
		};

		const message = ref('Hello Vue!');

		return {
			counter,
			increment,

			message,
		};
	},
};
</script>

<style></style>

<template>
	<div>
		<h1>템플릿 문법</h1>
		<hr />
		<h2>보간법</h2>
		<!--{{ xxx }}갱신됨-->
		<p>{{ message }}</p>
		<!-- v-once: 갱신 안됨.-->
		<p v-once>{{ message }}</p>
		<button @click="increment">click</button>
		<hr />
		<h2>v-html</h2>
		<p>{{ rawHtml }}</p>
		<p v-html="rawHtml"></p>
		<hr />
		<!--이중괄호는 HTML 속성에 바인딩할 수 없다 v-bind를 살펴보자-->
		<h2>속성 바인딩</h2>
		<div v-bind:title="dynamicTitle">마우스를 올려보세요</div>
		<!-- v-bind의 단축표현 :(콜론) -->
		<input type="text" value="홍길동" :disabled="isDisabled" />
		<!-- v-bind 다중속성 바인딩 -->
		<input v-bind="attr" />
		<hr />
		<h2>JavaScript 표현식</h2>
		{{ message.split('').reverse().join('') }}
		<br />
		{{ isInputDisabled ? '비활성화' : '활성화' }}
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		//이중괄호, v-once
		const message = ref('안녕하세요');
		const increment = () => {
			message.value = message.value + '!';
		};

		//v-html
		const rawHtml = ref('<strong>안녕하세요</strong>');

		//v-bind
		const dynamicTitle = ref('동적 속성 바인딩');
		const isDisabled = ref(true);
		const attr = ref({
			type: 'password',
			value: '123456789',
			disabled: false,
		});

		return {
			message,
			increment,
			rawHtml,
			dynamicTitle,
			isDisabled,
			attr,
		};
	},
};
</script>

<style></style>

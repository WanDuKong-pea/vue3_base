<template>
	<div>
		<!-- 
			클래스 바인딩.
			:class="{ 클래스명: 조건 }"
			조건이 true이면 클래스명이 적용되고, false이면 클래스명이 적용되지 않는다.
			기존에 적용한 클래스와 함께 사용 가능하다.
			클래스 적용 우선순위는 :class 가 더 높다

			:class 명에 특수문자가 들어가면 ''로 감싸줘야 한다.
			:class="{ 'text-danger': hasError }"
			
			:class에 여러개의 클래스를 바인딩 가능하다. 
			:class="{ 클래스명: 조건, 클래스명: 조건 }"
		-->
		<div class="size" :class="{ active: isActive, 'text-danger': hasError }">
			안녕하세요
		</div>
		<button @click="toggle">toggle</button>
		<button @click="mkError">error</button>
		<hr />
		<div :class="classObject"></div>
		<hr />
		<!--
			class명 배열에 삼항연산자 등 자바스크립트 표현식을 사용할 수 있다.
		-->
		<div :class="[isActive ? 'active-class' : 'class', errorClass]"></div>
	</div>
</template>

<script>
import { ref, computed } from 'vue';
export default {
	setup() {
		const isActive = ref(true);
		const toggle = () => {
			isActive.value = !isActive.value;
		};

		const hasError = ref(false);
		const mkError = () => {
			hasError.value = !hasError.value;
		};

		// const classObject = reactive({
		// 	active: true,
		// 	'text-danger': true,
		// });

		const classObject = computed(() => {
			return {
				active: true,
				'text-danger': true,
			};
		});

		const activeClass = ref('active');
		const errorClass = ref('error');

		return {
			isActive,
			toggle,
			hasError,
			mkError,
			classObject,
			activeClass,
			errorClass,
		};
	},
};
</script>

<style>
.size {
	height: 100px;
	background-color: lightgray;
}

.active {
	height: 100px;
	background-color: lightblue;
}

.text-danger {
	font-weight: bold;
	color: red;
}
</style>

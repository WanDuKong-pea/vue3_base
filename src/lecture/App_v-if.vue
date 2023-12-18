<template>
	<div>
		<!--
			v-if는 조건부 렌더링을 위한 디렉티브이다.
			v-else와 v-else-if는 v-if와 함께 사용되어야 한다.
		-->
		<p v-if="visible">Hello World</p>
		<p v-else>False 입니다.</p>
		<button @click="visible = !visible">Toggle</button>

		<hr />

		<h2 v-if="text === 'A'">A입니다.</h2>
		<h2 v-else-if="text === 'B'">B입니다.</h2>
		<h2 v-else-if="text === 'C'">C입니다.</h2>
		<h2 v-else>A,B,C가 아닙니다.</h2>
		<button @click="text = 'A'">A</button>
		<button @click="text = 'B'">B</button>
		<button @click="text = 'C'">C</button>
		<button @click="text = 'F'">F</button>

		<hr />

		<!-- div를 사용하지 않고 template을 사용하면 감싸는 요소 없이 태그를 렌더링 가능 -->
		<template v-if="visible">
			<h2>제목</h2>
			<p>내용</p>
		</template>

		<hr />

		<!-- 
			v-show:  개발자 도구로 봤을때, 렌더링은 되어 있으나, display:none 속성으로 렌더링 되는 것
			v-if: 개발자 도구로 봤을때, 렌더링이 되어 있지 않음
			무언가를 자주 전환해야 한다면 v-show를 사용하는 게 좋고, 
			런타임 시 조건이 변경되지 않는다면 v-if를 사용하는 게 더 좋음.
		-->
		<h1 v-show="ok">Hello Show</h1>
		<button @click="ok = !ok">Show_Toggle</button>

		<hr />
		<!--
			추가 정보
			v-if와 v-for를 같이 사용할 때는 v-for가 먼저 실행된다.
			따라서 v-if와 v-for를 같은 요소에 사용하지 않는 것이 좋다.
			template을 사용하여 v-for를 감싸면 v-if와 v-for를 같이 사용할 수 있다.-->
	</div>
</template>

<script>
import { ref } from 'vue';
export default {
	setup() {
		const visible = ref(true);
		const text = ref('A');
		const ok = ref(true);
		return {
			visible,
			text,
			ok,
		};
	},
};
</script>

<style></style>

<template>
	<div>
		<!--
			인라인 스타일을 적용할때는
			:style="{ color: 'red', fontSize: '20px' }" 혹은
			:style="styleObject" 와 같이 상용한다.
		-->
		<div :style="styleObject">
			Lorem, ipsum dolor sit amet consectetur adipisicing elit. Veniam modi
			nulla odit temporibus omnis dolore corporis dolorum a similique sequi
			dicta, aspernatur, voluptate culpa necessitatibus aliquid voluptatibus,
			nam obcaecati saepe?
		</div>
		<button @click="fontSize++">+</button>
		<button @click="fontSize--">-</button>
	</div>
</template>

<script>
import { computed, ref } from 'vue';
export default {
	setup() {
		// style에 인라인 스타일을 적용할 때 객체를 사용한다. -> reactive
		// 일반적으로 객체에 css 속성명을 적을때는 카멜케이스를 사용한다.
		// const styleObject = reactive({
		// 	color: 'red',
		// 	fontsize: '13px',
		// });

		const fontSize = ref(13);

		// 의문점: reactive와 computed의 차이점은 무엇인가?
		// reactive는 객체 자체를 반응형으로 만듬.
		// computed는 종속성 추적(dependency tracking)을 사용하여 종속성이 변경될 때만 재평가. 관련 부분만 다시 렌더링.
		// styleObject가 reactive로 만들어졌다면 속성 중 하나가 변경될 때마다 전체 객체가 변경되므로 불필요한 렌더링이 발생할 수 있음.
		// 이를 방지하기 위해 computed를 사용하여 필요한 속성만 변경될 때만 재평가되고 렌더링되도록 할 수 있음.
		// 일반적으로 computed를 사용하여 필요한 속성의 변경에만 반응하도록 코드를 작성하는 것이 권장됨.
		const styleObject = computed(() => {
			return {
				color: 'red',
				fontSize: fontSize.value + 'px',
			};
		});

		return {
			styleObject,
			fontSize,
		};
	},
};
</script>

<style lang="scss" scoped></style>

<!--
	반응형을 잃지 않고 구조분해 할당을 하는 방법을 배워보자
	toRef(), toRefs()
-->
<template>
	<div>
		<p>author: {{ author }}</p>
		<p>title: {{ title }}</p>
	</div>
</template>

<script>
import { reactive, toRefs, toRef } from 'vue';

export default {
	setup() {
		const book = reactive({
			author: 'Vue Team',
			year: '2020',
			title: 'Vue 3 Guide',
			description: '당신은 지급 바로 이 책을 읽습니다 :)',
			price: '무료',
		});

		//구조 분해 할당
		//구조 분해 할당 시 author, title과 같은 변수에 book 객체의 author, title의 값이 재할당 된 것
		//따라서 반응형이 유지되지 않는다.
		//const { author, title } = book;
		//console.log(typeof author); //string, 반응형을 잃어버림

		//반응성을 잃지 않고 구조분해 할당을 하는 방법
		//toRef(), toRefs()
		const { author, title } = toRefs(book);
		const year = toRef(book, 'year');
		const description = toRef(book, 'description');
		const price = toRef(book, 'price');

		return {
			author,
			title,
			year,
			description,
			price,
			book,
		};
	},
};
</script>

<style lang="scss" scoped></style>

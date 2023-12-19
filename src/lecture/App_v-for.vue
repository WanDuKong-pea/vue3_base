<template>
	<div>
		<ul>
			<li v-for="(item, index) in items" :key="item.id">
				인덱스: {{ index }}, {{ item.name }}
			</li>
		</ul>

		<!--
			v-for와 v-if 같이 사용해보기
		-->
		<template v-for="item in items" :key="item.id">
			<p v-if="item.id % 2 === 0">{{ item.name }} 짝수입니다.</p>
		</template>

		<hr />

		<!--
			배열에 filter를 사용하여 짝수만 출력해보기
		-->
		<ul>
			<li v-for="(i, index) in evenItems" :key="i.id">
				인덱스: {{ index }}, {{ i.name }}
			</li>
		</ul>

		<hr />
		<!--
			객체를 v-for로 순회하기	
			value, key, index 순으로 순회한다.		
		-->
		<ul>
			<li v-for="(value, key, index) in myObject" :key="key">
				{{ index }} : {{ key }} : {{ value }}
			</li>
		</ul>
	</div>
</template>

<script>
import { reactive, computed } from 'vue';
export default {
	setup() {
		const items = reactive([
			{ id: 1, name: 'Item 1' },
			{ id: 2, name: 'Item 2' },
			{ id: 3, name: 'Item 3' },
			{ id: 4, name: 'Item 4' },
		]);

		//배열에 filter를 사용하여 짝수만 출력해보기
		const evenItems = computed(() => items.filter(item => item.id % 2 === 0));

		const myObject = reactive({
			title: '제목',
			author: '홍길동',
			published: '2016-01-01',
		});

		return {
			items,
			evenItems,
			myObject,
		};
	},
};
</script>

<style></style>

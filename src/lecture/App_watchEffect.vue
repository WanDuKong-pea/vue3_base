<template>
	<div>
		<form action="" @submit.prevent>
			<input v-model.lazy="title" type="text" placeholder="title" />
			<textarea v-model.lazy="contents" placeholder="content"></textarea>
			<button @click="save(title, contents)">save</button>
		</form>
		<br />
		<hr />
	</div>
</template>

<script>
import { ref, watchEffect } from 'vue';
export default {
	setup() {
		const title = ref('');
		const contents = ref('');

		const save = (title, contents) => {
			console.log(`save ${title} ${contents}`);
		};

		//watchEffect는 의존하는 데이터가 변경될 때마다 실행됨
		//watch와 다르게 최초 렌더링 시점에도 실행됨 ,(watch의 immediate:true와 같음)
		//watch는 명ㅅ적으로 의존하는 데이터를 지정해야 하지만 watchEffect는 의존하는 데이터를 추적하여 자동으로 감지함
		//즉 watchEffect는 콜백함수 내부에서 의존하는 데이터를 사용하면 자동으로 의존하는 데이터를 추적함(명시적으로 의존하는 데이터를 지정할 필요가 없음)
		watchEffect(() => {
			console.log('watchEffect');
			save(title.value, contents.value);
		});

		return {
			title,
			contents,
			save,
		};
	},
};
</script>

<style></style>

<template>
	<div></div>
</template>

<script>
import { reactive, ref, watch } from 'vue';
export default {
	setup() {
		const x = ref(0);
		const y = ref(0);

		//watch에 첫번째 매개변수로 getter 함수를 넣어줌으로써 x,y 두수의 합을 감지할 수 있음
		// watch(
		// 	() => x.value + y.value, //getter
		// 	(sum, oldValue) => {
		// 		console.log('sum: ', sum);
		// 		console.log('oldValue: ', oldValue);
		// 	},
		// );

		//watch 감지 데이터를 배열로 입력할 수 있음
		//oldValue와 newValue를 각각 배열로 받아옴
		// watch([x, y], ([newX, newY], [oldX, oldY]) => {
		// 	console.log(newX, newY);
		// 	console.log(oldX, oldY);
		// });

		//reactive 오브젝트 타입 반응형 객체를 watch 감지 데이터로 입력할 수 있음
		const obj = reactive({
			count: 0,
		});

		//객체의 경우 watch의 첫번째 매개변수로 객체를 넣어주면
		//객체의 모든 프로퍼티를 감지하게 됨
		//또한 객체의 경우 oldValue와 newValue가 모두 같은 객체를 참조하게 됨(주소값이 같음)
		// watch(obj, newObj => {
		// 	console.log('newObj: ', newObj);
		// });

		//객체의 특정 프로퍼티만 감지하고 싶을 경우
		//watch의 첫번째 매개변수로 getter 함수를 넣어줌으로써 특정 프로퍼티만 감지할 수 있음
		//getter함수의 경우 getter 함수로 받아온 값이 변경되었느냐 아니냐를 감지하는 것
		// watch(
		// 	() => obj.count,
		// 	(newCount, oldCount) => {
		// 		console.log('newCount: ', newCount);
		// 		console.log('oldCount: ', oldCount);
		// 	},
		// );

		const person = reactive({
			name: 'Kim',
			age: 20,
			obj: {
				a: 1,
			},
		});

		//reactive를 사용한 객체의 경우 watch의 첫번째 매개변수로 객체를 넣어주면
		//객체의 모든 프로퍼티를 감지하게 됨
		watch(person, newPerson => {
			console.log('newPerson: ', newPerson);
		});

		//person의 obj 프로퍼티 내부의 a 프로퍼티를 감지하고 싶을 경우
		//person.obj.a를 getter 함수로 넣어줘야 함.
		//아래의 경우 obj 값 자체가 변경되어야 감지됨.
		// watch(
		// 	() => person.obj,
		// 	newPersonObj => {
		// 		console.log('newPersonObj: ', newPersonObj);
		// 	},
		// );

		return {
			x,
			y,
			obj,
			person,
		};
	},
};
</script>

<style></style>

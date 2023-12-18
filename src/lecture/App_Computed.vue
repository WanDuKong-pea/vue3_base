<!--
	computed를 이용한 반응형 데이터 다루기
	computed(()=>{}) : 함수를 인자로 받는다.
	computed({}) : 객체를 인자로 받는다.
-->
<template>
	<div>
		<h2>{{ teacher.name }}</h2>
		<h3>강의가 있습니까?</h3>
		<p>{{ teacher.lectures.length > 0 ? '있음' : '없음' }}</p>
		<!-- computed 는 data 변경이 없다면 한번 계산된 결과를 cache하기 떄문에 여러번 쓰일때 method보다 성능면에서 좋음-->
		<p>{{ hasLectures }}</p>
		<p>{{ hasLectures }}</p>
		<p>{{ hasLectures }}</p>
		<!-- method는 data 변경이 있든 없든, 호출할떄 마다 다시 계산됨. -->
		<p>{{ existLectures() }}</p>
		<p>{{ existLectures() }}</p>
		<p>{{ existLectures() }}</p>
		<button @click="counter++">Counter: {{ counter }}</button>
		<hr />
		<p>{{ fullName }}</p>
	</div>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
	setup() {
		const teacher = reactive({
			name: '짐코딩',
			lectures: ['HTML/CSS', 'JavaScript', 'Vue3'],
		});

		// computed는 data와 마찬가지로 template에서 사용할 수 있다.
		// data가 변경되지 않으면 computed는 다시 계산되지 않는다.
		// data가 변경되면 computed는 다시 계산된다.
		// data가 변경되지 않았는데도 computed가 다시 계산되는 것을 방지하기 위해 캐싱을 사용한다.
		// 캐싱은 data가 변경되면 다시 계산되고, data가 변경되지 않으면 이전에 계산된 값을 사용한다.
		// 캐싱을 사용하면 성능을 최적화할 수 있다.
		const hasLectures = computed(() => {
			//데이터 변경이 없을 때 캐싱을 사용하기 때문에 console.log가 한번만 찍힘
			console.log('computed');
			return teacher.lectures.length > 0;
		});

		// method는 data와 마찬가지로 template에서 사용할 수 있다.
		// data가 변경되면 method는 다시 계산된다.
		// data가 변경되지 않아도 method는 다시 계산된다.
		// method는 캐싱을 사용하지 않는다.
		const existLectures = () => {
			console.log('method');
			return teacher.lectures.length > 0;
		};

		const counter = ref(0);

		// computed는 get과 set을 사용하여 값을 가져오고 설정할 수 있다.
		// get과 set을 사용하지 않으면 computed는 읽기 전용이다.
		const firstName = ref('홍');
		const lastName = ref('길동');

		const fullName = computed({
			//computed로 함수가 아닌 객체를 정의하고 get과 set을 설정한다.
			get() {
				//computed로 설정한 객체의 get method는 즉 computed의 fullName을 호출할 때 실행된다.
				return firstName.value + ' ' + lastName.value;
			},
			set(value) {
				//하단 코드인 fullName.value = '짐 코딩'; 을 실행하면 computed의 set method가 실행된다.
				console.log('value', value);
				//value는 '짐 코딩'이다.
				console.log(value.split(' '));
				//받아온 value를 공백을 기준으로 나눈다. ['짐', '코딩']
				//배열의 첫번째 요소를 firstName에, 두번째 요소를 lastName에 할당한다.
				[firstName.value, lastName.value] = value.split(' ');
			},
		});
		console.log('콘솔출력', fullName.value);
		fullName.value = '짐 코딩';
		console.log('콘솔출력', fullName.value);

		return {
			teacher,
			hasLectures,
			existLectures,
			counter,
			fullName,
		};
	},
};
</script>

<style></style>

<template>
	<div>
		<h2>CheckBox</h2>
		<label for="chk1">단방향 checkbox v-bind:checked {{ chkValue1 }}</label>
		<input type="checkbox" id="chk1" :checked="chkValue1" />
		<br />
		<label for="chk2"
			>양방향 checkbox v-bind:checked, @change {{ chkValue2 }}</label
		>
		<input
			type="checkbox"
			id="chk2"
			:checked="chkValue2"
			@change="event => (chkValue2 = event.target.checked)"
		/>
		<br />
		<label for="chk3">양방향 checkbox v-model {{ chkValue3 }}</label>
		<input type="checkbox" id="chk3" v-model="chkValue3" />
		<br />
		<p>양방향 checkbox v-model, 배열 {{ chkValue4 }}</p>
		<label> <input type="checkbox" v-model="chkValue4" value="A" />A형</label>
		<label> <input type="checkbox" v-model="chkValue4" value="B" />B형</label>
		<label> <input type="checkbox" v-model="chkValue4" value="AB" />AB형</label>
		<label> <input type="checkbox" v-model="chkValue4" value="O" />O형</label>
		<br />
		<h2>Radio</h2>
		<h4>단방향 v-bind:checked</h4>
		<p>라디오 값: {{ radioValue1 }}</p>
		<label>
			<input
				type="radio"
				name="type1"
				value="O"
				:checked="radioValue1 === 'O'"
			/>
			O형
		</label>
		<label>
			<input
				type="radio"
				name="type1"
				value="A"
				:checked="radioValue1 === 'A'"
			/>
			A형
		</label>
		<br />
		<h4>양방향 v-bind:checked, @change</h4>
		<p>라디오 값: {{ radioValue2 }}</p>
		<label>
			<input
				type="radio"
				name="type2"
				value="O"
				:checked="radioValue2 === 'O'"
				@change="event => (radioValue2 = event.target.value)"
			/>
			O형
		</label>
		<label>
			<input
				type="radio"
				name="type2"
				value="A"
				:checked="radioValue2 === 'A'"
				@change="event => (radioValue2 = event.target.value)"
			/>
			A형
		</label>
		<br />
		<h4>양방향 v-model</h4>
		<p>라디오 값: {{ radioValue3 }}</p>
		<label>
			<input type="radio" name="type3" value="O" v-model="radioValue3" />
			O형
		</label>
		<label>
			<input type="radio" name="type3" value="A" v-model="radioValue3" />
			A형
		</label>
		<br />
		<hr />
		<h2>Select</h2>
		<h4>단방향 Select v-bind</h4>
		<p>혈액형: {{ selectValue1 }}</p>
		<select v-model="selectValue1">
			<!--select :value="selectValue1" @change="event => (selectValue1 = event.tart.value)"-->
			<option value="O">O형</option>
			<option value="A">A형</option>
			<option value="B">B형</option>
			<option value="AB">AB형</option>
		</select>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const chkValue1 = ref(true);
		const chkValue2 = ref(true);
		const chkValue3 = ref(true);
		const chkValue4 = ref([]);

		const radioValue1 = ref('O');
		const radioValue2 = ref('O');
		const radioValue3 = ref('O');

		const selectValue1 = ref('O');

		return {
			chkValue1,
			chkValue2,
			chkValue3,
			chkValue4,
			radioValue1,
			radioValue2,
			radioValue3,
			selectValue1,
		};
	},
};
</script>

<style></style>

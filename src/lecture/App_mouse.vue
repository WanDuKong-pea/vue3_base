<template>
	<div>
		<div id="modifiers">
			<div @click.capture="clickDiv">
				DIV
				<p @click.capture="clickP">
					P
					<!-- event.stopPropagation === @click.stop -->
					<!-- <span @click.stop="clickSpan"> SPAN </span> -->
					<span @click="clickSpan"> SPAN </span>
					<span @click.once="clickSpan"> SPAN </span>
				</p>
			</div>
		</div>
		<!-- event.preventDefault() === @click.prevent -->
		<a href="https://www.naver.com" @click.prevent="clickA">NAVER</a>
	</div>
</template>

<script>
export default {
	setup() {
		const clickDiv = () => {
			console.log('clickDiv');
			//location.href = 'https://www.naver.com';
		};
		const clickP = () => {
			console.log('clickP');
		};
		const clickSpan = () => {
			//event.stopPropagation();
			console.log('clickSpan');
			//alert('좋아요');
		};
		const clickA = () => {
			alert('clickA');
		};

		return {
			clickDiv,
			clickP,
			clickSpan,
			clickA,
		};
	},
};
</script>

<style>
#modifiers div,
#modifiers p,
#modifiers span {
	padding: 40px;
	font-size: 40px;
	font-weight: bold;
}

#modifiers div {
	background-color: #ccc;
}

#modifiers p {
	background-color: #999;
}

#modifiers span {
	background-color: #666;
	display: block;
}
</style>

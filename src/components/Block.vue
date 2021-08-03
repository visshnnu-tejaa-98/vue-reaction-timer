<template>
	<h4 class="block" @click="end" v-if="showBlock">Click Here..</h4>
</template>

<script>
export default {
	props: ['delay'],
	data() {
		return {
			showBlock: false,
			reactionTime: 0,
			timer: 0,
		};
	},
	methods: {
		// end() {
		// 	this.$emit('end');
		// },
		startTime() {
			this.timer = setInterval(() => {
				this.reactionTime += 10;
			}, 10);
		},
		end() {
			clearInterval(this.timer);
			console.log(this.reactionTime);
			this.$emit('end', this.reactionTime);
		},
	},
	mounted() {
		setTimeout(() => {
			this.showBlock = true;
			this.startTime();
			console.log(this.delay);
		}, this.delay);
	},
};
</script>

<style>
.block {
	background-color: teal;
	color: white;
	padding: 10% 7%;
	width: 400px;
	margin: 20px auto;
	border-radius: 20px;
}
</style>

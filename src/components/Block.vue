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
		startTime() {
			this.timer = setInterval(() => {
				this.reactionTime += 10;
			}, 10);
		},
		end() {
			clearInterval(this.timer);
			this.$emit('end', this.reactionTime);
		},
	},
	mounted() {
		setTimeout(() => {
			this.showBlock = true;
			this.startTime();
		}, this.delay);
	},
};
</script>

<style>
.block {
	background-color: #3f7b81;
	color: white;
	padding: 7%;
	width: 300px;
	height: 150px;
	margin: 20px auto;
	border-radius: 20px;
	display: flex;
	justify-content: center;
	align-items: center;
}
</style>

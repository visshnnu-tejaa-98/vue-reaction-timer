<template>
	<div class="home">
		<h1>Reaction Timer</h1>
		<button @click="startGame" :disabled="isPlaying">Play</button>
		<Block v-if="isPlaying" @end="endGame" :delay="delay" />
		<Result :score="score" v-if="showResult" />
	</div>
</template>

<script>
import Block from '../components/Block.vue';
import Result from '../components/Result.vue';
export default {
	components: { Block, Result },
	props: ['reactionTime'],
	data() {
		return {
			isPlaying: false,
			delay: null,
			score: 0,
			showResult: false,
		};
	},
	methods: {
		startGame() {
			this.isPlaying = true;
			this.showResult = false;
			this.delay = Number((Math.random() * 5000 + 2000).toString().split('.')[0]);
			console.log(this.isPlaying, this.delay);
		},
		endGame(time) {
			this.score = time;
			this.isPlaying = false;
			this.showResult = true;
			console.log(this.score);
		},
	},
};
</script>

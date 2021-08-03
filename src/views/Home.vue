<template>
	<div class="home">
		<p class="h1">Reaction Timer</p>
		<p class="des">
			click the displayed block as fast as you can after a random time period of 2 to 7 sec...
		</p>
		<br />
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
		},
		endGame(time) {
			this.score = time;
			this.isPlaying = false;
			this.showResult = true;
		},
	},
};
</script>

<style>
body {
	background-color: #2f5d62;
	font-family: monospace;
	padding: 0;
	margin: 0;
	box-sizing: border-box;
	width: 400px;
	margin: 0 auto;
}
.h1 {
	font-size: 2.5rem;
	font-weight: bold;
	color: #dfeeea;
}
button {
	background-color: #5e8b7e;
	padding: 0.5% 1.5%;
	border: none;
	color: #dfeeea;
	font-size: 1.3rem;
	font-family: monospace;
	font-weight: bold;
	cursor: pointer;
}
button:hover {
	background-color: #81bdac;
}
button:disabled {
	background-color: #bcc0bf;
	cursor: not-allowed;
}
.des {
	color: wheat;
}
</style>

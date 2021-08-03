<template>
	<h4>
		Reaction Time : <span>{{ score }}ms</span>
	</h4>
	<h3 class="status">{{ status }}</h3>
</template>

<script>
export default {
	props: ['score'],
	data() {
		return {
			status: '',
		};
	},
	mounted() {
		if (this.score < 350) {
			this.status = 'Ninja Fingers';
		} else if (this.score < 550) {
			this.status = 'Super Fast';
		} else {
			this.status = 'Snail Peace';
		}
	},
};
</script>

<style>
.status {
	color: teal;
}
h4 {
	color: #81bdac;
	font-size: 1.1rem;
}
h3 {
	color: #dfeeea;
	padding: 2%;
	background-color: #c2e5db;
	font-size: 1.3rem;
}
h4 span {
	color: #dfeeea;
}
</style>

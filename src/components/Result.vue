<template>
	<h4>Reaction Time : {{ score }}ms</h4>
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
	mounted(){
      if (this.score < 350) {
         this.status = 'Ninja Fingers';
      } else if (this.score < 550) {
         this.status = 'Super Fast';
      } else {
         this.status = 'Snail Peace';
      }
   }
};
</script>

<style>
.status {
	color: teal;
}
</style>

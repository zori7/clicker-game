<template>
	<div class="text-center">
		<button style="border-radius: 20px 20px 0 0; width: 200px" class="btn btn-info btn-lg" @click="increment"><i class="fas fa-money-bill-wave fa-3x"></i></button>
	</div>
</template>

<script>
	export default {
		name: 'click',
		data: function () {
			return {
				cash: 0
			}
		},
		methods: {
			increment () {
				this.$eventHub.$emit('click-increment');
			}
		}
	}
</script>

<style>
	
</style>

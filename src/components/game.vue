<template>
	<div class="container">
		<div class="mt-4 d-flex">
			<div class="flex-grow-1">
				
			</div>
			<div class="text-center flex-grow-1">
				<div>
					<h2>Ваш счёт:</h2>
				<h3><i class="fas fa-dollar-sign"></i> {{ roundCash }}</h3>
				</div>
				<div>
					<h3>Автоматически + {{ roundIncrement }}/сек</h3>
				</div>
			</div>
			<div class="d-flex flex-column align-items-center flex-grow-1">
				<button class="btn btn-primary btn-lg btn-block" style="width: 150px" @click="openShop"><i class="fas fa-shopping-bag fa-2x"></i></button>
				<div class="font-weight-bolder mt-2">
					Магазин
				</div>
			</div>
		</div>
		<shop ref="shop" :cash="cash"></shop>
	</div>
</template>

<script>
	import shop from './shop';
	export default {
		name: 'game',
		components: {
			shop
		},
		data: function () {
			return {
				cash: 0,
				increment: 0
			}
		},
		computed: {
			roundCash () {
				return this.roundToThree(this.cash);
			},
			roundIncrement () {
				return this.roundToThree(this.increment);
			}
		},
		mounted () {
			this.$eventHub.$on('click-increment', () => {
				this.cash++;
			});
			this.$eventHub.$on("buy", (item) => {
				this.increment += item.increment;
				this.cash -= item.price;
			});
			setInterval(() => {
				this.cash += this.increment / 10;
			}, 100);
		},
		methods: {
			openShop () {
				this.$refs.shop.visible = true;
			},
			roundToThree (num) {
				return +(Math.round(num + "e+3")  + "e-3");
			}
		}
	}
</script>

<style>
	
</style>

<template>
	<el-dialog
	title="Магазин"
	:visible.sync="visible"
	width="60%"
	top="30vh">
	<button :disabled="cash < item.price" class="btn btn-primary btn-block" :key="item.id" v-for="item in items" @click="buy(item)">
		<div class="float-left ml-4"><i :class="'fas fa-' + item.icon + ' fa-lg'"></i></div>
		{{ item.name }} - 
		Купить за $ {{ roundToThree(item.price) }}
		+ {{ roundToThree(item.increment) }}/сек
		(у вас - {{ item.count }})
	</button>
	</el-dialog>
</template>

<script>
	export default {
		name: 'shop',
		props: ['cash'],
		data: function () {
			return {
				visible: false,
				items: [
					{
						id: 1,
						name: 'Курсор',
						icon: 'mouse-pointer',
						increment: 0.001,
						price: 0.1,
						count: 0
					},
					{
						id: 2,
						name: 'Видеокарта',
						icon: 'memory',
						increment: 0.003,
						price: 1,
						count: 0
					},
					{
						id: 3,
						name: 'Стойка видеокарт',
						icon: 'layer-group',
						increment: 0.01,
						price: 5,
						count: 0
					},
					{
						id: 4,
						name: 'Суперкомпьютер',
						icon: 'server',
						increment: 0.03,
						price: 10,
						count: 0
					},
					{
						id: 5,
						name: 'Сервер ВКонтакте',
						icon: 'table',
						increment: 0.1,
						price: 100,
						count: 0
					},
					{
						id: 6,
						name: 'Квантовый компьютер',
						icon: 'microchip',
						increment: 0.5,
						price: 500,
						count: 0
					},
					{
						id: 7,
						name: 'Датацентр',
						icon: 'database',
						increment: 1,
						price: 1000,
						count: 0
					},
				]
			}
		},
		methods: {
			increment () {
				this.$eventHub.$emit('click-increment');
			},
			buy(item){
                this.$eventHub.$emit("buy", item);
                let i = this.items.find(obj => obj.id === item.id);
                i.price *= 1.3;
                i.count++;
			},
			roundToThree (num) {    
				return +(Math.round(num + "e+3")  + "e-3");
			}
		}
	}
</script>

<style>
	
</style>

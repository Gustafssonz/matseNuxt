<template>
	<div>
		<div v-if="dataProps.length > 1" class="searchbox">
			<v-text-field v-model="msg"> </v-text-field>
		</div>

		<div class="productsbox">
			<Product
				v-for="product in filteredProducts"
				:product="product"
				:key="product.id"
			/>
		</div>
	</div>
</template>

<script>
export default {
	props: ["dataProps"],
	data() {
		return {
			msg: "",
		};
	},
	computed: {
		filteredProducts: function () {
			return this.dataProps.filter((product) =>
				product.name.toLowerCase().includes(this.msg.toLowerCase())
			);
		},
	},
};
</script>

<style>
.productsbox {
	display: flex;
	align-content: flex-start;
	flex-wrap: wrap;
}
</style>
<template>
	<div>
		<div v-if="dataProps.length > 1" class="searchbox">
			<!-- <Searchbox :productList="data" /> -->
			<!-- @click="filterObject" -->
			<!-- <input v-model="message" placeholder="edit me"> -->
			<v-text-field v-model="msg"> </v-text-field>
		</div>
		<div class="productsbox">
			<Product
				v-for="product in filteredProducts"
				:product="product"
				:key="product.name"
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
			if (this.msg == "") {
				return this.dataProps;
			} else {
                // Solution 1, not working
				/* return this.dataProps.filter((product) => {
					product.name.toLowerCase().includes(this.msg.toLowerCase());
				}); */
                // Solution 2, working.
                var newArray = []
				this.dataProps.filter((product) => {
					if (product.name.toLowerCase().includes(this.msg.toLowerCase())) {
						newArray.push(product);
					}
				});
				return newArray;
			}
		},
	},
	methods: {
		refresh() {
			console.log(this.dataProps);
		},
	},
};
</script>

<style>
.productsbox {
	display: flex;
	align-content: flex-start;
	/* flex-direction: row; */
	flex-wrap: wrap;
}
</style>
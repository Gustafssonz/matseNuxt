<template>
	<div>
		<div v-if="dataProps" class="searchbox">
			<!-- <Searchbox :productList="data" /> -->

			<!-- <input v-model="message" placeholder="edit me"> -->
			<v-text-field v-model="msg"> </v-text-field>
			<v-btn elevation="2" @click="filterObject">{{ msg }}</v-btn>
		</div>
		<div class="productsbox">
			<Product
				v-for="(product, index) in dataObject"
				:product="product"
				:key="index"
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
            dataObject: this.dataProps,
		};
	},
	methods: {
		filterObject(msg) {
			this.dataProps.filter((product) => product.name.includes(this.msg));
            this.refresh();
			return this.dataProps;
		},
        refresh() {
            this.$nuxt.refresh()
        }
	},
};
</script>

<style>
.productsbox {
	display: flex;
	flex-direction: row;
	flex-wrap: wrap;
}
</style>
<template>
	<div>
		<div v-if="dataProps" class="searchbox">
			<!-- <Searchbox :productList="data" /> -->
			<!-- @click="filterObject" -->
			<!-- <input v-model="message" placeholder="edit me"> -->
			<v-text-field v-model="msg"> </v-text-field>
			<v-btn elevation="2" @click="refresh">{{ msg }}</v-btn>
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
			msg: '',
		};
	},
	computed: {
		filteredProducts: function () {
			if (this.msg == '') {
				return this.dataProps;
			} else {
				var newArray = [];
                this.dataProps.filter((product) => {
                    if(product.name.toLowerCase().includes(this.msg.toLowerCase())){
                    newArray.push(product);
                    }
				});
                console.log(newArray);
                return newArray;
			}
		},
	},
	methods: {
		refresh() {
            console.log(this.dataProps)
		},
	},
};
</script>

<style>
.productsbox {
	display: flex;
	align-content: flex-start;
	/* flex-direction: row; */
	/* flex-wrap: wrap; */
}
</style>
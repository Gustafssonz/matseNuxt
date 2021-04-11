<template>
	<div class="container">
		<div class="nav-drawer">
				<CategoryMenu :data="categories.subCategories" @emitToParent="getProducts"/>
		</div>
		<div class="results" v-if="products" >
				<Result :data="products" />
		</div>
		</div>
	</div>
</template>

<script>
export default {
	data: () => {
		return {
			categories: [],
			selectedCategory: null,
			products: [],
		};
	},
	async fetch() {
		this.categories = await fetch(
			"https://matse.futurememories.se/getCategoryTree"
		).then((res) => res.json());
	},
	// async fetch() {
	// 	this.categories = await fetch("https://matse.futurememories.se/getCategoryTree")
	// 	console.log(categories)
	// }
	methods: {
		async getProducts(categoryId) {
			console.log("getting products with catId ", categoryId);
			this.products = await fetch(
			`https://matse.futurememories.se/listByCategory?categoryId=${categoryId}`
		).then((res) => res.json());
		},
		 onEmitChildValue (value) {
      this.selectedCategory = value
			console.log("Child to Parent with value ", this.selectedCategory)
    }
	}
};
</script>

<style>
.container {
	margin: 0 auto;
	display: flex;
}
.nav-drawer{
	flex-grow: 20%;
}

.results{
}
</style>

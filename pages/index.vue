<template>
	<div class="container">
		<div class="nav-drawer">
				<CategoryMenu :data="categories.subCategories" @emitToParent="getProducts"/>
		</div>
		<div class="results" v-if="products" >
				<Result :dataProps="products" />
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
	methods: {
		async getProducts(categoryId) {
			console.log("getting products with catId ", categoryId);
			this.products = await fetch(
			`https://matse.futurememories.se/listByCategory?categoryId=${categoryId}`
		).then((res) => res.json().then(console.log(res)));
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
	margin-left: 12px;
	width: 100%;
}
</style>

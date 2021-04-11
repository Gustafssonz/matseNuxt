<template>
	<div class="container">
		<div class="nav-drawer">
				<CategoryMenu :data="categories.subCategories" />
		</div>
		<div>
			<div>
			</div>
			<!-- <p v-if="$fetchState.pending">Fetching categories...</p>
			<div v-else>
				<div v-for="categoryData of categories.subCategories" @click="getProducts(categoryData.id)">
					<Category :data="categoryData" />
				</div>
				<button @click="$fetch">Refresh</button>
			</div> -->

			<div v-if="products">
				<div v-for="product in products">
					<Result :data="product" />
				</div>
			</div>

		</div>
	</div>
</template>

<script>
export default {
	data: () => {
		return {
			categories: [],
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
			this.products = await fetch(
			`https://matse.futurememories.se/listByCategory?categoryId=${categoryId}`
		).then((res) => res.json());
		}
	}
};
</script>

<style>
.container {
	margin: 0 auto;
	display: flex;
	width: 100%;
	justify-content: center;
	align-items: center;
	text-align: center;
}

.title {
	font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
		"Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
	display: block;
	font-weight: 300;
	font-size: 100px;
	color: #35495e;
	letter-spacing: 1px;
}

.subtitle {
	font-weight: 300;
	font-size: 42px;
	color: #526488;
	word-spacing: 5px;
	padding-bottom: 15px;
}

.links {
	padding-top: 15px;
}
</style>

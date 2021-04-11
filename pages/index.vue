<template>
	<div class="container">
		<div>
			<p v-if="$fetchState.pending">Fetching categories...</p>
			<div v-else>
				<h1>Nuxt Mountains</h1>
				<ul>
					<li v-for="categoryData of categories.subCategories">
						<Category :category="categoryData" />
					</li>
				</ul>
				<button @click="$fetch">Refresh</button>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	data: () => {
		return {
			categories: [],
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
};
</script>

<style>
.container {
	margin: 0 auto;
	min-height: 100vh;
	display: flex;
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

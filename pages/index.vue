<template>
	<div class="container">
		<div>
			<p v-if="$fetchState.pending">Fetching categories...</p>
			<!-- <p v-else-if="$fetchState.error">An error occurred :(</p> -->
			<div>
				<h1>Nuxt Category</h1>
					<h1 v-if="categories">{{categories.name}} HDSA</h1>
					<div v-if="categories">
						dsa
						<div v-for="category in categories" >
									<Category :data="category" />
						</div>
					</div>
				<button @click="$fetch">Refresh c</button>
			</div>

			<p v-if="data"> Exist data </p>
			{{ data }}
			</div>
		</div>
	</div>
</template>

<script>
export default {
	data: () => {
		return {
			categories: [],
			data: null
		};
	},
	async fetch() {
		categories = await fetch(
			"https://matse.futurememories.se/getCategoryTree"
		).then((res) => res.json().then(res => console.log(res)));
	},
	mounted () {
    axios
      .get('https://matse.futurememories.se/getCategoryTree')
      .then(response => (this.data = response))
  }
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

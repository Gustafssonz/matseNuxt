<template>
	<div>
        <div class="searchbox">
            <!-- Searchbox -->
        </div>
		<div class="productsbox">
			<Product v-for="product in data" :product="product" />
		</div>
	</div>
</template>

<script>
export default {
	props: ["data"],
	data() {
		return {};
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
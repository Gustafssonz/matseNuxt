<template>
	<div>
        <div v-for="product in data">
            <Product class="products" :product="product" />
        </div>
	</div>
</template>

<script>
export default {
	props: ["data"],
	data() {
		return {
		};
	},
};
</script>

<style>
.products{
    flex-direction: row;
    flex-wrap: wrap;
}
</style>
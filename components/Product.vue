<template>
	<v-card class="mx-auto card">
		<v-img :src="product.imageUrl"></v-img>
		<v-card-title> {{product.name}} </v-card-title>
	</v-card>
</template>

<script>
export default {
	props: ["product"],
	data() {
		return {};
	},
};
</script>

<style>
.card{
	margin: 10px;
	width: 20%

}

@media only screen and (max-width: 1200px) {
	.card {
		width: 25%
	}
}

@media only screen and (max-width: 768px) {
	.card {
		width: 50%
	}
}
</style>

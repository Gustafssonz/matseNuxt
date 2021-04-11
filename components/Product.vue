<template>
	<v-card class="mx-auto" max-width="244" max-height="300">
		<v-img :src="product.imageUrl" height="100px"></v-img>
		<v-card-title> {{product.name}} </v-card-title>
		<v-card-subtitle> </v-card-subtitle>

		<!-- <v-card-actions>
			<v-btn color="orange lighten-2" text> Explore </v-btn>

			<v-spacer></v-spacer>

			<v-btn icon @click="show = !show">
				<v-icon>{{ show ? "mdi-chevron-up" : "mdi-chevron-down" }}</v-icon>
			</v-btn>
		</v-card-actions>

		<v-expand-transition>
			<div v-show="show">
				<v-divider></v-divider>

				<v-card-text>
					{{product.content}}
				</v-card-text>
			</div>
		</v-expand-transition> -->
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
</style>

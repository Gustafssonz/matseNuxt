<template>
	<v-card class="mx-auto">
		<v-navigation-drawer permanent>
			<v-list>
				<div v-for="item in data">
					<template v-if="item.subCategories.length > 1">
						<!-- v-for="item in data" -->
						<v-list-group :key="item.name" v-model="item.active" no-action>
							<template v-slot:activator>
								<v-list-item-content @click="fetchProducts(item.id)">
									<v-list-item-title v-text="item.name"></v-list-item-title>
								</v-list-item-content>
							</template>
							<div v-if="item.subCategories">
								<CategoryMenu :data="item.subCategories" />
							</div>
						</v-list-group>
					</template>
					<template v-else>
						<v-list-item :key="item.name" @click="fetchProducts(item.id)">
							<v-list-item-content>
								<v-list-item-title v-text="item.name"></v-list-item-title>
							</v-list-item-content>
						</v-list-item>
						 </v-btn>

					</template>
				</div>
			</v-list>
		</v-navigation-drawer>
	</v-card>
</template>

<script>
export default {
	props: ["data"],
	data: () => ({}),
	methods: {
		fetchProducts(categoryId) {
			console.log(categoryId)
		},
	},
};
</script>

<style>
.title {
	font-size: 18px;
}
</style>
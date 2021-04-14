<template>
	<v-card>
		<v-navigation-drawer permanent>
			<v-list>
				<div v-for="item in data">
					<template v-if="item.subCategories.length > 1">
						<!-- v-for="item in data" -->
						<v-list-group :key="item.name" v-model="item.active" no-action>
							<template v-slot:activator>
								<!-- @click="emitToParent(item.id)" -->
								<v-list-item-content  @click="selectedCategory(item.id)">
									<v-list-item-title v-text="item.name"></v-list-item-title>
								</v-list-item-content>
							</template>
							<div v-if="item.subCategories">
								<CategoryMenu :data="item.subCategories" @emitToParent="selectedCategory"/>
							</div>
						</v-list-group>
					</template>
					<template v-else>
						<v-list-item class="submenu" :key="item.name" @click="selectedCategory(item.id)" >
							<v-list-item-content >
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
	data: () => ({
	}),
	methods: {
		selectedCategory(categoryId) {
			this.$emit('emitToParent', categoryId)
		},
	},
};
</script>

<style>
.title {
	font-size: 18px;
}
.submenu{
	background-color: rgb(244, 244, 244);
}
</style>
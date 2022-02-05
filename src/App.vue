<template>
	<v-app>
		<v-app-bar app>
			<v-toolbar-title class="mr-5">Ферма</v-toolbar-title>
			<v-toolbar-title>Илья Безбах 201-322</v-toolbar-title>
		</v-app-bar>

		<v-navigation-drawer app>
			<v-list>
				<v-list-item
					v-for="(item, i) in items"
					:key="i"
					:to="item.to"
					router
					exact
				>
					<v-list-item-action>
						<v-icon>{{ item.icon }}</v-icon>
					</v-list-item-action>
					<v-list-item-content>
						<v-list-item-title v-text="item.title" />
					</v-list-item-content>
				</v-list-item>
			</v-list>

			<v-subheader>В нашем роддоме родилось:</v-subheader>

			<v-list-item>
				<v-list-item-content>
					<v-list-item-title
						>Добрейших коровок:
						{{ widgetStats.cows }}</v-list-item-title
					>
				</v-list-item-content>
			</v-list-item>
			<v-list-item>
				<v-list-item-content>
					<v-list-item-title
						>Милейших кроликов:
						{{ widgetStats.rabbits }}</v-list-item-title
					>
				</v-list-item-content>
			</v-list-item>

			<v-list-item>
				<v-list-item-content>
					<v-list-item-title
						>Пушистейших овечек:
						{{ widgetStats.sheeps }}</v-list-item-title
					>
				</v-list-item-content>
			</v-list-item>

			<!--<WidgetStats />-->
		</v-navigation-drawer>

		<v-main>
			<v-container class="pa-10">
				<router-view />
			</v-container>
		</v-main>
	</v-app>
</template>

<script>
	import axios from 'axios'

		export default {
			name: 'DefaultLayout',
			data() {
				return {
	                widgetStats: {},

					items: [
						{
							icon: 'mdi-home-outline',
							title: 'Главная',
							to: '/',
						},
						{
							icon: 'mdi-account-box-outline',
							title: 'О нас',
							to: '/about',
						},
						{
							icon: 'mdi-view-list',
							title: 'Список животных',
							to: '/animals',
						},
					],
				}
			},

	        async mounted() {
	            this.widgetStats = (await axios('https://demo-api.vsdev.space/api/farm/left_widget')).data
	        }
		}
</script>

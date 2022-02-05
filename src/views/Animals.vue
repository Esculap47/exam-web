<template>
	<div class="wrapper">
        <MyForm />
		<MyCard v-for="animal in animals" :key="animal.id" :animal="animal"/>
	</div>
</template>

<script>
	import MyCard from '../components/MyCard.vue'
	import MyForm from '../components/MyForm.vue'

	export default {
		components: { MyForm, MyCard },

		async mounted() {
			await this.$store.dispatch('fetchAnimals')
		},

		computed: {
			animals() {
				return this.$store.state.animals
			},
		},
	}
</script>

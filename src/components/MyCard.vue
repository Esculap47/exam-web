<template>
	<v-card>
		<v-img
			:src="`/${animal.type}_img.jpg`"
			class="white--text align-end"
			gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
			height="250"
		>
			<v-card-title>{{ animal.name }}</v-card-title>
		</v-img>

		<v-card-text class="text-left">
			<div>Цвет</div>
			<p class="text--primary">{{ animal.color }}</p>

			<div>Вес</div>
			<p class="text--primary">{{ animal.weight }}кг</p>

			<div>Пол</div>
			<p class="text--primary">{{ animal.sex }}</p>
		</v-card-text>
	</v-card>
</template>

<script>
	export default {
		props: ['animal'],
	}
</script>

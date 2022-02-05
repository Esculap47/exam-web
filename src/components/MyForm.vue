<template>
	<div>
		<v-select
			v-model="type"
			:items="['cow', 'rabbit', 'sheep']"
			label="Тип животного"
			required
		></v-select>
		<v-text-field v-model="name" label="Имя" required></v-text-field>

		<v-text-field v-model="weight" label="Вес" required></v-text-field>

		<v-text-field v-model="color" label="Цвет" required></v-text-field>

		<v-select
			v-model="sex"
			:items="['Девочка', 'Мальчик']"
			label="Пол"
			required
		></v-select>

		<v-btn
			color="success"
			class="mb-15 mt-5"
			@click="handleForm"
			width="100%"
		>
			Добавить
		</v-btn>
	</div>
</template>

<script>
import axios from 'axios'

	export default {
		data: () => ({
			type: 'cow',
			name: '',
			weight: '',
			color: '',
			sex: '',
		}),

		methods: {
			async handleForm() {
                try {
 				const data = {
					type: this.type,
					name: this.name,
					weight: this.weight,
					color: this.color,
					sex: this.sex,
				}

                await axios.post('https://demo-api.vsdev.space/api/farm/baby', data)
                
                } catch (e) {
                    console.log(e);
                }

			},
		},
	}
</script>

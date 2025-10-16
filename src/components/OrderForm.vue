<template>
	<section class="order-form container">
		<form @submit.prevent="onSubmit" class="order-form__form">
			<!-- Сетка из первых 3 полей -->
			<FormField
				v-for="field in orderFields"
				:key="field.name"
				:field="field"
				v-model="formData[field.name]"
			/>

			<!-- Остальные поля (range, file и т.п.) -->
			<div class="order-form__group">
				<div class="order-form__range-header">
					<span class="order-form__range-title"
						>Sed ut perspiciatis, unde omnis iste</span
					>
					<span class="order-form__range-value">{{ formData.progress }}%</span>
				</div>

				<FormField
					v-for="field in orderRange"
					:key="field.name"
					:field="field"
					v-model="formData[field.name]"
				/>
			</div>
			<FormField
				v-for="field in orderImage"
				:key="field.name"
				:field="field"
				v-model="formData[field.name]"
				@file-change="handleFileChange"
			/>

			<!-- Кнопка отправки -->
			<BaseButton
				backgroundColor="#3e9cdc"
				color="#ffffff"
				type="submit"
				customClass="order-form__button"
			>
				Заказать
			</BaseButton>
		</form>
	</section>
</template>

<script setup>
import { reactive } from 'vue';
import FormField from './FormField.vue';
import BaseButton from '@/components/BaseButton.vue';

// Поля формы
const fields = [
	{
		type: 'select',
		name: 'topic',
		placeholder: 'Выберите тип системы',
		required: true,
		options: [
			{ value: 'design', text: 'Sed ut perspiciatis' },
			{ value: 'dev1', text: 'Nemo enim ipsam' },
			{ value: 'dev2', text: 'Et harum quidem' },
			{ value: 'dev3', text: 'Temporibus autem' },
			{ value: 'dev4', text: 'Itaque earum rerum' },
		],
	},
	{ name: 'email', type: 'email', placeholder: 'Ваш email', required: true },
	{ name: 'name', type: 'text', placeholder: 'Ваше имя', required: true },
	{ name: 'progress', type: 'range', min: 0, max: 100, default: 75 },
	{ name: 'attachment', type: 'file', placeholder: 'Прикрепить файл' },
];

// Разделение для layout
const orderFields = fields.slice(0, 3);
const orderRange = fields.slice(3, 4);
const orderImage = fields.slice(4);
// Автоматическое создание реактивных значений
const formData = reactive({});
fields.forEach((field) => {
	formData[field.name] = field.default ?? (field.type === 'file' ? null : '');
});

// Обработка выбора файла
function handleFileChange(event) {
	const file = event.target.files[0];
	formData.attachment = file;
}

// Обработка отправки формы
function onSubmit() {
	console.log('Отправка формы:', formData);
	alert('Форма отправлена!');
}
</script>

<style lang="scss" scoped>
.order-form {
	margin-bottom: 150px;

	&__form {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		gap: 30px;

		@include media-tablet {
			display: flex;
			flex-direction: column;
		}

		@include media-mobile {
			display: flex;
			flex-direction: column;
		}
	}

	&__group {
		align-self: end;
		grid-column: span 2;

		@include media-tablet {
			align-self: auto;
		}

		@include media-mobile {
			align-self: auto;
		}
	}

	&__button {
		grid-column: 2 / 3;
	}

	&__range-header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin-bottom: 8px;
	}

	&__range-title {
		font-weight: 400;
		font-size: 18px;
		color: #ffffff;
	}

	&__range-value {
		font-weight: 600;
		font-size: 18px;
		color: rgba(255, 255, 255, 0.85);
	}
}
</style>

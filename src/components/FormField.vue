<template>
	<div :class="['form-field', customClass]">
		<!-- Select -->
		<select
			v-if="field.type === 'select'"
			:name="field.name"
			:required="field.required"
			:value="modelValue"
			@input="$emit('update:modelValue', $event.target.value)"
			class="form-field__select"
		>
			<option value="" disabled>{{ field.placeholder }}</option>
			<option
				v-for="(option, i) in field.options"
				:key="i"
				:value="option.value"
			>
				{{ option.text }}
			</option>
		</select>

		<!-- Text Inputs -->
		<input
			v-else-if="field.type !== 'file' && field.type !== 'range'"
			:type="field.type"
			:name="field.name"
			:placeholder="field.placeholder"
			:required="field.required"
			:value="modelValue"
			@input="$emit('update:modelValue', $event.target.value)"
			class="form-field__input"
		/>

		<!-- Range -->
		<input
			v-else-if="field.type === 'range'"
			type="range"
			:name="field.name"
			:value="modelValue"
			@input="$emit('update:modelValue', $event.target.value)"
			:style="rangeStyle"
			class="form-field__range"
			:min="field.min"
			:max="field.max"
			:step="field.step"
		/>

		<!-- File -->
		<label v-else class="form-field__file">
			<input
				ref="fileInput"
				type="file"
				:name="field.name"
				@change="onFileChange"
				class="form-field__file-input"
			/>
			<span
				:class="[
					'form-field__file-display',
					{ 'form-field__file-display--selected': selectedFileName },
				]"
				><span class="form-field__file-icon" aria-hidden="true"></span>
				<span
					class="form-field__file-text"
					:title="selectedFileName || field.placeholder"
				>
					{{ selectedFileName || field.placeholder }}
				</span>

				<button
					v-if="selectedFileName"
					type="button"
					class="form-field__file-clear-btn"
					@click.prevent="clearFile"
					aria-label="Очистить файл"
				>
					✕
				</button>
			</span>
		</label>
	</div>
</template>

<script setup>
import { ref, watch, computed } from 'vue';

const props = defineProps({
	field: { type: Object, required: true },
	modelValue: [String, Number, File, null],
	customClass: { type: String, default: '' },
});

const emit = defineEmits(['update:modelValue', 'file-change']);

const fileInput = ref(null);
const selectedFileName = ref('');

// Обновляем имя файла, если модель изменилась извне
watch(
	() => props.modelValue,
	(newVal) => {
		selectedFileName.value = newVal instanceof File ? newVal.name : '';
	},
	{ immediate: true },
);

function onFileChange(event) {
	const file = event.target.files[0];
	selectedFileName.value = file ? file.name : '';
	emit('update:modelValue', file || null);
	emit('file-change', event);
}

function clearFile() {
	selectedFileName.value = '';
	emit('update:modelValue', null);
	if (fileInput.value) fileInput.value.value = null;
}

const rangeStyle = computed(() => {
	if (props.field.type !== 'range') return {};
	const value = Number(props.modelValue) || 0;
	const min = Number(props.field.min ?? 0);
	const max = Number(props.field.max ?? 100);
	const percent = (value - min) / (max - min) * 100;
	return {
		background: `linear-gradient(to right, #a19a9a ${percent}%, rgba(255, 255, 255, 0.7) ${percent}%)`,
	};
});
</script>

<style scoped lang="scss">
.form-field {
	display: flex;
	gap: 8px;

	&__select,
	&__input,
	&__range {
		width: 100%;
		padding: 10px 12px;
		font-size: 18px;
		color: #272733;
		background-color: rgba(255, 255, 255, 0.85);
		border: 1px solid #ffffff;
		border-radius: 3px;
		outline: none;
	}

	&__range {
		height: 6px;
		padding: 0;
		background-color: #cccccc;
		border-radius: 3px;
		cursor: pointer;
		appearance: none;

		&::-webkit-slider-thumb,
		&::-moz-range-thumb,
		&::-ms-thumb {
			width: 24px;
			height: 24px;
			background: no-repeat center/cover var(--icon-circle);
			border: none;
			cursor: pointer;
			appearance: none;
		}
	}

	&__file {
		display: flex;
		align-items: center;
		width: 100%;

		&-input {
			display: none;
		}

		&-display {
			display: flex;
			justify-content: center;
			align-items: center;
			width: 100%;
			padding: 10px 12px;
			background: white;
			border: 2px solid #3e9cdc;
			border-radius: 3px;
			cursor: pointer;

			&--selected {
				justify-content: space-between;
			}
		}

		.button {
			display: flex;
			padding: 1rem;
			color: red;
		}

		&-icon {
			width: 20px;
			height: 20px;
			margin-right: 10px;
			background: no-repeat center/contain var(--icon-add-file);

			.form-field__file-display--selected & {
				display: none;
			}
		}

		&-text {
			text-align: center;
		}

		&-clear-btn {
			display: flex;
			justify-content: center;
			align-items: center;
			width: 24px;
			height: 24px;
			margin-left: 10px;
			font-size: 18px;
			color: #000000;
			background: transparent;
			border: none;
			cursor: pointer;
		}
	}
}
</style>

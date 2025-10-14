<template>
	<button
		:class="['base-button', { 'base-button--outlined': outlined }, customClass]"
		:style="buttonStyles"
		v-bind="$attrs"
		@click="handleMoreClick"
	>
		<slot />
	</button>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
	backgroundColor: { type: String, default: '#3e9cdc' },
	color: { type: String, default: '#ffffff' },
	padding: { type: String, default: '15px 50px' },
	fontSize: { type: String, default: '13px' },
	fontWeight: { type: String, default: '400' },
	outlined: { type: Boolean, default: false },
	customClass: { type: String, default: '' },
});

const emit = defineEmits(['click']);

const buttonStyles = computed(() => ({
	backgroundColor: props.outlined ? '#ffffff' : props.backgroundColor,
	color: props.outlined ? props.backgroundColor : props.color,
	border: `1px solid ${props.outlined ? props.backgroundColor : '#ffffff'}`,
	borderRadius: '4px',
	padding: props.padding,
	cursor: 'pointer',
	fontWeight: props.fontWeight,
	fontSize: props.fontSize,
	textAlign: 'center',
	userSelect: 'none',
	transition:
		'background-color 0.3s ease, color 0.3s ease, box-shadow 0.2s ease',
}));

function handleMoreClick(event) {
	emit('click', event);
}
</script>

<style scoped>
.base-button {
	display: inline-block;
	box-sizing: border-box;
	line-height: 1;
	text-transform: uppercase;
	border-radius: 4px;
	outline: none;
}

.base-button:focus-visible {
	outline: none;
	box-shadow: 0 0 0 3px rgba(62, 156, 220, 0.5);
	transition: box-shadow 0.2s ease;
}
</style>

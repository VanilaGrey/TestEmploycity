<template>
	<component :is="tag" class="icon-text" :style="buttonStyles" v-bind="$attrs">
		<span class="icon-text__icon" aria-hidden="true"></span>
		<span v-if="$slots.default" class="icon-text__text">
			<slot />
		</span>
	</component>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
	icon: { type: String, required: true },
	count: { type: Number, default: null },
	as: { type: String, default: 'button' },
	color: { type: String, default: null },
});

const tag = props.as;

const buttonStyles = computed(() => ({
	...props.color ? { color: props.color } : {},
	'--icon': `var(--icon-${props.icon})`,
}));
</script>

<style scoped lang="scss">
.icon-text {
	position: relative;
	display: flex;
	align-items: center;
	font-weight: 400;
	font-size: 13px;
	color: #ffffff;
	background-color: transparent;
	border: none;
	cursor: pointer;
	gap: 10px;

	&__icon {
		display: block;
		flex-shrink: 0;
		width: 20px;
		height: 20px;
		height: 1lh;
		background-color: #3e9cdc;
		mask: var(--icon);
		mask-repeat: no-repeat;
		mask-size: contain;
	}
}
</style>

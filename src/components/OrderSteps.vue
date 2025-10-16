<template>
	<div class="steps">
		<div v-for="(step, index) in steps" :key="index" class="steps__item">
			<div class="steps__icon">
				<div
					:class="['steps__icon-image', `steps__icon-image--${step.icon}`]"
				></div>
			</div>
			<div class="steps__text">{{ step.text }}</div>

			<div v-if="index !== steps.length - 1" class="steps__separator"></div>
		</div>
	</div>
</template>

<script setup>
const steps = [
	{ icon: 'search', text: 'Lorem ipsum dolor sit amet' },
	{ icon: 'percent', text: 'Consectetur adipiscing elit' },
	{ icon: 'file', text: 'Sed do eiusmod tempor' },
	{ icon: 'message', text: 'Esse cillum dolore eu fugiat' },
	{ icon: 'money', text: 'Excepteur sint occaecat cupidatat non proident' },
];
</script>

<style scoped lang="scss">
.steps {
	position: relative;
	display: flex;
	flex-wrap: wrap;
	margin-bottom: 80px;
	overflow-x: hidden;
	gap: 30px;

	@include media-tablet {
		justify-content: center;
	}

	@include media-mobile {
		justify-content: center;
	}

	&__separator {
		position: absolute;
		top: 30%;
		left: 75%;
		width: 130px;
		height: 6px;
		background-image: radial-gradient(circle, #c4c4c4 3px, transparent 3px);
		background-repeat: repeat-x;
		background-size: 26px 6px;

		@include media-tablet {
			display: none;
		}

		@include media-mobile {
			display: none;
		}
	}

	&__item {
		position: relative;
		display: flex;
		flex-shrink: 0;
		flex-direction: column;
		align-items: center;
		width: 209px;
		text-align: center;

		&:last-child .steps__separator {
			display: none;
		}
	}

	&__icon {
		position: relative;
		display: flex;
		justify-content: center;
		align-items: center;
		width: 100px;
		height: 100px;
		background-color: transparent;
		background-image: var(--icon-circle);
		background-repeat: no-repeat;
		background-position: center;
		background-size: contain;
		border-radius: 50%;

		&-image {
			width: 55px;
			height: 55px;
			background-repeat: no-repeat;
			background-position: center;
			background-size: contain;

			&--search {
				background-image: var(--icon-search);
			}

			&--percent {
				background-image: var(--icon-percent);
			}

			&--file {
				background-image: var(--icon-file);
			}

			&--message {
				background-image: var(--icon-message);
			}

			&--money {
				background-image: var(--icon-money);
			}
		}
	}

	&__text {
		margin-top: 10px;
		padding: 0 10px;
		font-weight: 400;
		font-size: 16px;
		color: #ffffff;

		@include media-tablet {
			font-size: 14px;
			text-align: center;
		}

		@include media-mobile {
			font-size: 12px;
			text-align: center;
		}
	}
}
</style>

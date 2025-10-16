<script setup>
import BaseButton from '@/components/BaseButton.vue';

const items = [
	'Totam rem aperiam eaque ipsa',
	'Sit voluptatem accusantium doloremque laudantium',
	'Sed ut perspiciatis, unde omnis iste natus error',
];

function handleOrderClick() {
	console.log('Заказ оформлен');
}

function handleMoreClick() {
	console.log('Подробнее нажато');
}
</script>

<template>
	<section class="preview">
		<img
			class="preview__image"
			src="/images/foto-1.jpg"
			alt="foto-1"
			width="100%"
			height="100%"
		/>
		<div class="container">
			<div class="preview__content">
				<h1 class="preview__title heading heading--xl">
					<span class="heading__highlight">LOREM IPSUM</span> DOLOR SIT<br />
					<span class="heading__highlight">AMET</span> CONSECTETUR
					<span class="heading__highlight">ADIPISCING</span>
				</h1>
				<p class="preview__label">
					At vero eos et accusamus et iusto odio dignissimos ducimus!
				</p>
				<ul class="preview__list">
					<li class="preview__item" v-for="(item, index) in items" :key="index">
						{{ item }}
					</li>
				</ul>
				<div class="preview__buttons">
					<BaseButton
						backgroundColor="#3e9cdc"
						color="#ffffff"
						@click="handleOrderClick"
					>
						Заказать
					</BaseButton>

					<BaseButton
						outlined
						backgroundColor="#000000"
						color="#000"
						@click="handleMoreClick"
					>
						Подробнее
					</BaseButton>
				</div>
			</div>
		</div>
	</section>
</template>

<style lang="scss" scoped>
.preview {
	position: relative;
	min-height: 850px;
	margin-bottom: 120px;
	overflow: hidden;

	&__image {
		position: absolute;
		inset: 0;
		width: 100%;
		max-width: none;
		height: 100%;
		object-fit: cover;
	}

	&__content {
		position: relative;
		max-width: 780px;
		padding: 203px 0 0;

		@include media-tablet {
			max-width: 400px;
		}

		@include media-mobile {
			max-width: 200;
			text-align: center;
		}
	}

	&__title {
		margin: 0 0 80px;

		@include media-tablet {
			text-align: center;
		}
	}

	&__label {
		margin: 0;
		font-weight: 700;
		font-size: 20px;
		color: #000000;

		@include media-tablet {
			font-size: 18px;
			text-align: center;
		}

		@include media-mobile {
			font-size: 18px;
		}
	}

	&__list {
		margin: 0 0 80px;
		padding: 0;
		list-style: none;
		text-align: left;
	}

	&__item {
		position: relative;
		padding-left: 20px;
		font-weight: 400;
		font-size: 20px;

		&::before {
			content: '-';
			position: absolute;
			left: 0;
			font-weight: bold;
			color: #000000;
		}

		@include media-tablet {
			font-size: 16px;
		}

		@include media-mobile {
			font-size: 16px;
		}
	}

	&__buttons {
		display: flex;
		gap: 30px;

		@include media-tablet {
			flex-direction: column;
		}

		@include media-mobile {
			flex-direction: column;
		}
	}
}
</style>

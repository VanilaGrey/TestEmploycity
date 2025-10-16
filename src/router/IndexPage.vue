<script setup>
import PreviewBlock from '@/components/PreviewBlock.vue';
import OrderSteps from '@/components/OrderSteps.vue';
import OrderForm from '@/components/OrderForm.vue';
</script>

<template>
	<main class="main">
		<div class="main__preview">
			<PreviewBlock />
		</div>
		<div class="main__order container">
			<h2 class="heading heading--lg">
				Оформление
				<span class="heading__highlight">заказа </span>
			</h2>
			<p class="main__order-text">
				Перед заполнением формы ознакомьтесь с нашей схемой работы!
			</p>
			<OrderSteps />
			<OrderForm />
		</div>
	</main>
</template>

<style scoped lang="scss">
.main {
	background-image: url('/images/background-1.jpg'); // Твоя фоновая картинка
	background-repeat: no-repeat;
	background-position: center;
	background-size: cover;

	&__order {
		text-align: center;

		&-text {
			margin: 30px 0 80px;
			font-weight: 400;
			font-size: 18px;
			color: #bbbbbb;
		}
	}
}
</style>

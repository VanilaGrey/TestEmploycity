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
		<OrderSteps />
		<OrderForm />
	</main>
</template>

<style scoped lang="scss">
.main {
	background-image: url("/images/background-1.jpg"); // Твоя фоновая картинка
	background-size: cover;
	background-position: center;
	background-repeat: no-repeat;
}
</style>

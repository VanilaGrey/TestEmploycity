<script setup>
import Preview from '@/components/Preview.vue';
import OrderSteps from '@/components/OrderSteps.vue';
import OrderForm from '@/components/OrderForm.vue';
</script>

<template>
	<main class="main">
		<div class="main__preview">
			<Preview />
		</div>
		<OrderSteps />
		<OrderForm />
	</main>
</template>

<style scoped lang="scss">
.main {
	background-image: url('/images/background-1.jpg'); // Твоя фоновая картинка
	background-repeat: no-repeat;
	background-position: center;
	background-size: cover;
}
</style>

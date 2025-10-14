<script setup>
import BaseLogo from './BaseLogo.vue';
import MenuList from './MenuList.vue';
</script>

<template>
	<header class="header">
		<div class="header__inner container">
			<BaseLogo />
			<MenuList />
		</div>
	</header>
</template>

<style scoped lang="scss">
.header {
	position: fixed;
	z-index: 1;
	width: 100%;
	padding: 33px 0;
	color: #ffffff;
	background-color: rgba(16, 16, 29, 0.9);

	@include media-tablet {
		padding: 20px 0;
	}

	@include media-mobile {
		padding: 10px 0;
	}

	&__inner {
		display: flex;
		align-items: center;
	}
}
</style>

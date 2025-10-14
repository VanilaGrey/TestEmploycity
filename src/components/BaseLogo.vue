<script setup>
const MoveOnIndex = () => {
	window.location.href = 'index.html';
};
</script>

<template>
	<img @click="MoveOnIndex" class="logo" src="/images/logo.png" alt="logo" />
</template>

<style scoped lang="scss">
.logo {
	width: 248px;
	height: 100%;
	cursor: pointer;

	@include media-tablet {
		width: 130px;
	}

	@include media-mobile {
		width: 120px;
	}
}
</style>

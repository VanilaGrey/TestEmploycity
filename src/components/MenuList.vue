<script setup>
const menuItems = ['Бизнес', 'О нас', 'Цены', 'Оформить заказ'];
</script>

<template>
	<nav class="menu">
		<ul class="menu__list">
			<li v-for="item in menuItems" :key="item" class="menu__item">
				<a class="menu__link" href="#!">{{ item }}</a>
			</li>
		</ul>
	</nav>
</template>

<style scoped lang="scss">
.menu {
	margin-left: auto;
	padding-left: 40px;
}

.menu__list {
	display: flex;
	flex-wrap: wrap;
	justify-content: center;
	align-items: center;
	margin: 0;
	padding: 0;
	list-style-type: none;
	gap: 60px;

	@include media-tablet {
		gap: 15px;
	}

	@include media-mobile {
		gap: 10px;
	}
}

.menu__item {
	display: flex;
	align-items: center;
}

.menu__link {
	font-weight: 700;
	font-size: 13px;
	color: inherit;
	text-transform: uppercase;
	text-decoration: none;

	@include media-tablet {
		font-size: 10px;
	}

	@include media-mobile {
		font-size: 6px;
	}

	&:hover,
	&:focus,
	&:active {
		color: #43abf0;
	}
}
</style>

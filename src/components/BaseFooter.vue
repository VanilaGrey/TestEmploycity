<template>
	<footer class="footer">
		<div class="footer__container container">
			<span class="footer__copyright">
				© 2018 LOREMIPSUM.NET. Все права защищены.
			</span>
			<div class="footer__payment">
				<IconText icon="qiwi" color="#c3c3c3">QIWI Wallet</IconText>
				<IconText icon="yandex-money" color="#c3c3c3">Yandex Money</IconText>
				<IconText icon="web-money" color="#c3c3c3"> Web Money </IconText>
			</div>
			<div class="footer__links">
				<IconText icon="mail" as="a" href="mailto:info@ipsum228.com"
					>info@ipsum228.com</IconText
				>
				<IconText icon="vk" as="a" href="https://vk.com">Мы Вконтакте</IconText>
			</div>
		</div>
	</footer>
</template>

<script setup>
import IconText from './IconText.vue';
</script>

<style scoped lang="scss">
.footer {
	padding: 30px 0;
	font-weight: 400;
	font-size: 13px;
	background-color: #3d4050;

	&__container {
		display: grid;
		grid-template-columns: 1fr auto auto;
		gap: 0 38px;

		@include media-tablet {
			grid-template-columns: 1fr 1fr;
		}

		@include media-mobile {
			display: flex;
			flex-direction: column;
			gap: 10px;
		}
	}

	&__copyright {
		color: #ffffff;

		@include media-tablet {
			order: 3;
			grid-column: 1 / span 2;
			margin-top: 10px;
			text-align: center;
		}

		@include media-mobile {
			order: 3;
			grid-column: 1 / span 2;
			margin-top: 10px;
			text-align: center;
		}
	}

	&__payment {
		position: relative;
		display: flex;
		flex-wrap: wrap;
		padding: 0 38px;
		gap: 0 38px;

		&::before,
		&::after {
			content: '|';
			position: absolute;
			top: 50%;
			font-weight: normal;
			font-size: 16px;
			color: #c3c3c3;
			transform: translateY(-50%);
		}

		&::before {
			left: 0;
		}

		&::after {
			right: 0;
		}

		@include media-tablet {
			padding: 0 30px 0 0;
			gap: 10px;

			&::before {
				display: none;
			}
		}

		@include media-mobile {
			gap: 10px;
			padding: 0;

			&::before,
			&::after {
				display: none;
			}
		}
	}

	&__links {
		display: flex;
		flex-wrap: wrap;
		gap: 0 38px;

		@include media-tablet {
			gap: 10px;
		}
	}

	@include media-mobile {
		gap: 10px;
	}
}
</style>

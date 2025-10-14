<!-- <template>
  <section class="steps">
    <h2 class="steps__title">ОФОРМЛЕНИЕ <span>ЗАКАЗА</span></h2>
    <div class="steps__list">
      <div class="steps__item" v-for="(step, i) in steps" :key="i">
        <BaseIcon :id="step.icon" />
        <p>{{ step.text }}</p>
      </div>
    </div>
  </section>
</template>

<script setup>
const steps = [
	{ icon: 'icon-1', text: 'Lorem ipsum dolor sit amet' },
	{ icon: 'icon-2', text: 'Consectetuer adipiscing' },
	{ icon: 'icon-3', text: 'Sed do eiusmod tempor' },
	{ icon: 'icon-4', text: 'Duis aute irure dolor' },
	{ icon: 'icon-5', text: 'Excepteur sint occaecat' },
];
</script>

<style lang="scss" scoped>
.steps {
	padding: 40px 20px;
	color: #ffffff;
	background-color: #0f1216;

	&__title {
		margin-bottom: 20px;
		text-align: center;

		span {
			color: #4fa7ff;
		}
	}

	&__list {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-around;
		gap: 16px;
	}

	&__item {
		width: 100px;
		text-align: center;

		svg {
			width: 40px;
			height: 40px;
			margin-bottom: 8px;
		}

		p {
			font-size: 12px;
		}
	}
}
</style> -->


<!-- <template>
  <section class="order-form">
    <form @submit.prevent="onSubmit">
      <div class="order-form__group">
        <select name="topic" required>
          <option value="">Выберите тему</option>
          <option value="design">Дизайн</option>
          <option value="dev">Разработка</option>
        </select>

        <input type="email" name="email" placeholder="Ваш email" required />
        <input type="text" name="name" placeholder="Ваше имя" required />

        <input type="range" name="progress" />

        <label class="order-form__file">
          <input type="file" name="attachment" />
          <span>Прикрепить файл</span>
        </label>

        <button type="submit" class="btn btn--primary">Отправить</button>
      </div>
    </form>
  </section>
</template>

<script setup>
function onSubmit() {
	alert('Форма отправлена!');
}
</script>

<style lang="scss" scoped>
.order-form {
	padding: 40px 20px;
	background-color: #ffffff;

	&__group {
		display: flex;
		flex-direction: column;
		gap: 12px;

		select,
		input[type='text'],
		input[type='email'] {
			padding: 10px;
			font-size: 14px;
			border: 1px solid #cccccc;
			border-radius: 4px;
		}

		input[type='range'] {
			width: 100%;
		}

		&__file {
			display: flex;
			align-items: center;
			gap: 10px;

			input {
				display: none;
			}

			span {
				padding: 6px 10px;
				color: #2a76dd;
				border: 1px dashed #2a76dd;
				border-radius: 4px;
				cursor: pointer;
			}
		}
	}
}
</style> -->

<template>
  <div class="form__wrapper">
    <form id="form" action="" class="form">
      <base-field />
      <div
        v-for="(input, index) of formInputs"
        :key="index"
        class="form__input-wrapper"
      >
        <label class="form__input-label" :for="input.label">{{
          input.label
        }}</label>
        <input
          :id="input.label"
          v-model="input.value"
          class="form__input"
          :placeholder="input.placeholder"
          :type="input.type"
        />
      </div>

      <div class="form__input-wrapper">
        <label class="form__input-label" for="email">Email</label>
        <input
          id="email"
          v-model="form.email"
          class="form__input"
          placeholder="Обязательное поле"
          type="email"
        />
      </div>

      <div class="form__input-wrapper">
        <label class="form__input-label" for="phone">Телефон</label>
        <input
          id="phone"
          v-model="form.phone"
          class="form__input"
          placeholder="Обязательное поле"
          type="tel"
        />
      </div>

      <div class="form__input-wrapper">
        <label class="form__input-label" for="comment">Комментарий</label>
        <textarea
          id="comment"
          v-model="form.comment"
          class="form__input"
          placeholder="Необязательное поле"
        />
      </div>

      <div class="form__input-wrapper">
        <label class="form__input-label" for="agreement"
          >Согласие на обработку персональных данных</label
        >
        <input
          id="agreement"
          v-model="form.isAgreed"
          class="form__input"
          type="checkbox"
        />
      </div>

      <button type="submit" class="form__button-submit">Отправить</button>
    </form>
  </div>
</template>

<script>
import BaseField from './BaseField.vue';

export default {
  name: 'BaseForm',
  components: {
    BaseField
  },
  data() {
    return {};
  },

  methods: {}
};
</script>

<style lang="scss" scoped>
  .form {
    display: flex;
    flex-direction: column;

    &__wrapper {
      display: flex;
      justify-content: center;
    }

    &__input {
      &-wrapper {
        display: flex;
      }
    }
  }
</style>

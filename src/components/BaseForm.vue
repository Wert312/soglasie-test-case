<template lang="pug">
div
  template(v-if='!showMessage')
    .form__wrapper
      form#form(@submit.prevent='validateForm(formFields)')
        legend Анкета
        fieldset
          base-field(:form-fields='formFields')
          button.form__button-submit(type='submit') Отправить
  template(v-if='showMessage')
    .form__wrapper
      legend Анкета успешно отправлена!
        fieldset
          button.form__button-submit(@click='toggleMessage()') Отправить снова
</template>

<script>
import BaseField from './BaseField.vue';

export default {
  name: 'BaseForm',
  components: {
    BaseField
  },
  data() {
    return {
      showMessage: false,
      formFields: [
        {
          tag: 'input',
          id: 'name',
          type: 'text',
          label: 'ФИО',
          value: null,
          placeholder: 'Обязательное поле',
          required: true
        },
        {
          tag: 'input',
          id: 'email',
          type: 'email',
          label: 'Email',
          value: null,
          placeholder: 'Обязательное поле',
          required: true
        },
        {
          tag: 'input',
          id: 'phone',
          type: 'tel',
          label: 'Телефон',
          value: null,
          placeholder: 'Обязательное поле',
          required: true
        },
        {
          tag: 'textarea',
          id: 'commentary',
          label: 'Комментарий',
          value: null,
          placeholder: 'Необязательное поле',
          required: false
        },
        {
          tag: 'input',
          id: 'agreement',
          type: 'checkbox',
          label: 'Согласие на обработку персональных данных',
          value: null,
          required: true
        }
      ]
    };
  },

  methods: {
    validateForm() {
      const emptyRequiredFields = [];
      this.formFields.map(item => {
        if (item.required && !item.value) {
          emptyRequiredFields.push(item.label);
        }
      });

      if (emptyRequiredFields.length > 0) {
        alert(
          `Необходимо заполнить следующие поля: ${emptyRequiredFields.join(
            ', '
          )}`
        );
      } else {
        this.toggleMessage();
      }
    },

    toggleMessage() {
      this.showMessage = !this.showMessage;
      this.formFields.forEach(item => (item.value = null));
    }
  }
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
  }
</style>

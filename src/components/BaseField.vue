<template lang="pug">
div
  .field__input-wrapper(v-for='(item, index) of formFields', :key='index')
    template(v-if='item.tag === "input"')
      label.field__input-label(:for='item.id') {{ item.label }}
      input.field__input(
        :id='item.id',
        v-model='item.value',
        :placeholder='item.placeholder',
        :type='item.type'
      )
    template(v-if='item.tag === "textarea"')
      label.field__input-label(:for='item.id') {{ item.label }}
      textarea.field__input(
        :id='item.id',
        v-model='item.value',
        :placeholder='item.placeholder'
      )
</template>

<script>
export default {
  name: 'BaseField',
  props: {
    formFields: {
      type: Array,
      required: true,
      default() {
        [];
      }
    }
  }
};
</script>

<style lang="scss" scoped>
  .field {
    &__input {
      &-wrapper {
        display: grid;
        grid-template-columns: 1fr 1fr;
        margin-bottom: 20px;
        align-items: center;
      }

      &-label {
        width: 100%;
        text-align: left;
      }
    }
  }
</style>
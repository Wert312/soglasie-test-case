<template lang="pug">
div
  div.form__input-wrapper&attributes(v-for="(input, index) of formInputs" :key="index")
        label.form__input-label&attributes(:for="input.label")
          input.label
        input.form__input&attributes(:id="input.label" v-model="input.value" :placeholder="input.placeholder" :type="input.type")
        />
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
</style>
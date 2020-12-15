<template>
  <div id="app">
    <BaseForm />
  </div>
</template>

<script>
import BaseForm from './components/BaseForm.vue';

export default {
  name: 'App',
  components: {
    BaseForm
  }
};
</script>

<style lang="scss">
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>

<template>
  <div id="app">
    <h1>Vue.js Calculator</h1>
    <Calculator></Calculator>
    <h2>Mark Johnson</h2>
    <h3>
      <a href="http://hellomark.dev">hellomark.dev</a>
    </h3>
  </div>
</template>

<script>
import Calculator from "./components/Calculator.vue";

export default {
  name: "app",
  components: {
    Calculator
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

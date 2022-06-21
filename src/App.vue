<template>
  <img alt="Vue logo" src="./assets/logo.png">
  
  <!-- <Counter title="Salieron" /> -->
  <!-- <Counter v-bind:start="5"/> -->
  <!-- <Counter :start="5"/> este sirve para la validación con validator {} -->  
  <Counter /> 
 
</template>

<script>
import Counter from "./components/Counter.vue";

export default {
  name: 'App',
  components: {
    Counter
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

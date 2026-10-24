<template>
  <CalculadoraV msg="Calculadora Vue"/>
</template>

<script>
import CalculadoraV from './components/CalculadoraV.vue';

export default {
  name: 'App',
  components: {
    CalculadoraV
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

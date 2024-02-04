<template>
  <div id="app">
    <ButtonCity />
  </div>
</template>

<script>
import ButtonCity from './components/ButtonCity.vue'


export default {
  name: 'App',
  components: {
    ButtonCity
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

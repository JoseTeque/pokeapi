<template>
  <div id="app">
    <img class="img-logo" alt="Logo Pokemon" src="https://fontmeme.com/images/Pokemon-Logo.jpg">
    <PokeApi msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import PokeApi from './components/PokeApi.vue'

export default {
  name: 'App',
  components: {
    PokeApi
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
 
}

#app .img-logo{
  margin: 0;
  padding: 0;
  width: 300px;
  height: 300px;
}
</style>

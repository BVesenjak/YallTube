<template>
  <img alt="Vue logo" src="./assets/ytlogo.jpg">
  <ytSearch></ytSearch>
</template>

<script>
import ytSearch from './components/ytSearch.vue'

export default {
  name: 'App',
  components: {
    ytSearch
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

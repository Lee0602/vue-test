<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <configList msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import configList from './pages/list.vue'

export default {
  name: 'App',
  components: {
    configList
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

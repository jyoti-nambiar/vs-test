<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <ImageListMain msg="Welcome to Your Vue.js App"  @click="showModal"/>
  </div>
</template>

<script>
import ImageListMain from './components/ImageListMain.vue'

export default {
  name: 'App',
  components: {
    ImageListMain
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

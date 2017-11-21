<template>
  <div id="app">
    <img src="./assets/logo.png">
    <iviewlook/>
  </div>
</template>

<script>
import iviewlook from './components/iviewlook'
export default {
  name: 'app',
  components: {
    iviewlook
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

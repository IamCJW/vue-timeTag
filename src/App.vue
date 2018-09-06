<template>
  <div id="app">
    <img src="./assets/logo.png">
    <timeTag/>
  </div>
</template>

<script>
import timeTag from './components/timeTag'

export default {
  name: 'App',
  components: {
    timeTag
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

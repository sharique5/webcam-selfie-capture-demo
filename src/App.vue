<template>
  <div id="app">
    <WebcamCapture/>
  </div>
</template>

<script>
import WebcamCapture from './components/WebcamCapture.vue'

export default {
  name: 'App',
  components: {
    WebcamCapture
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

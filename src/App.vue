<template>
  <div id="app">
    <div class="color-picker-container">
      <color-picker></color-picker>
    </div>
    <hello></hello>
  </div>
</template>

<script>
import Hello from './components/Hello'
import ColorPicker from './components/ColorPicker'
export default {
  name: 'app',
  components: {
    Hello,
    ColorPicker
  }
}
</script>

<style>
#app {
  width: 100vw;
  height: 100vh;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.color-picker-container {
  width: 50%;
  height: 90%;
}
</style>

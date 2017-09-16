<template>
  <div id="app">
    <div class="color-picker-container">
      <color-picker v-model="color"></color-picker>
    </div>
    <div class="grid-container">
      <pixel-grid :current-color="color"></pixel-grid>
    </div>
    <!-- <hello></hello> -->
  </div>
</template>

<script>
import Hello from './components/Hello'
import ColorPicker from './components/ColorPicker'
import PixelGrid from './components/PixelGrid'
export default {
  name: 'app',
  data() {
    return {
      color: null   
    }
  },
  components: {
    Hello,
    ColorPicker,
    PixelGrid
  }
}
</script>

<style>
body {
  margin: 0;
  width: 100vw;
  height: 100vh;
}
#app {
  width: 100%;
  height: 100%;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
}

.color-picker-container {
  margin-top: 5%;
  width: 10%;
  height: 90%;
}
.grid-container {
    margin-top: 5%;
  height: 90%;
  width: 80%;
}
</style>

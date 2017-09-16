<template>
  <div id="app">
    <div class="color-picker-container">
      a{{color}}a
      <color-picker v-model="color"></color-picker>
      }
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
#app {
  width: 100vw;
  height: 100vh;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
}

.color-picker-container {
  width: 10%;
  height: 90%;
}
.grid-container {
  height: 90%;
  width: 80%;
}
</style>

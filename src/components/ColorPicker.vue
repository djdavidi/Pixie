<template>
  <div class="color-picker">
  <!-- need to add hex input -->
  <!-- need to add labels for ranges, and spacing and highlight on selected patch -->
  	<!-- <div class="range-container"> -->
		<input type="range" @change="calculateColor" v-model="hue">
		<input type="range"  @change="calculateColor" v-model="saturation">
		<input type="range"  @change="calculateColor" v-model="lightness">
	<!-- </div> -->
	<div :style="{background: calculateColor()}" class="current-color">&nbsp;</div>
  	<div class="color-patch-container">
		<div v-for="n in 12"  @click="setColorHue(n*30)" class="color-patch" :style="{background: 'hsl('+ n*30 +', 100%, 50%)'}">
			&nbsp;
		</div>
		<div class="color-patch black-patch" @click="setColorLightness(0)">&nbsp;</div>
		<div class="color-patch white-patch" @click="setColorLightness(100)">&nbsp;</div>
	</div>
  </div>
</template>

<script>
export default {
  name: 'colorpicker',
  data () {
    return {
      hue: 50,
      saturation: 100,
      lightness: 50
      // currentColor: this.calculateColor
    }
  },
  methods: {
  	calculateColor() {
  		console.log("this.hue", this.hue);
  		this.$emit("input",`hsl(${this.hue * 3.6}, ${this.saturation}%, ${this.lightness}%)`);
  		return `hsl(${this.hue * 3.6}, ${this.saturation}%, ${this.lightness}%)`;
  	},
  	setColorHue(hue) {
  		this.hue = hue/3.6;
  		this.saturation = 100;
  		this.lightness = 50;
  	},
  	setColorLightness(lightness) {
  		this.lightness = lightness;
  		this.calculateColor();
  	}
 //  	function (index, totalLength) {
	// var thing = 360/totalLength * index;
	// background-color: hsl(thing, 100%, 50%);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.color-picker {
	width: 100%;
	display: flex;
	flex-direction: column;
}

.current-color {
	height: 100px;
}
.color-patch-container {
	display: grid;
	width: 100%;
	grid-template-columns: 1fr  1fr;
}

input {
	width: 100%;
}

.color-patch {
	color: #fff;
	border: 5px solid #000;
}

.color-patch:hover {
	cursor: pointer;
}

.black-patch {
	background-color: #000;
}

.white-patch {
	background-color: #fff;
}
</style>

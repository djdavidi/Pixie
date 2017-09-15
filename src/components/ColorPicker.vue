<template>
  <div class="color-picker">
	<input type="range" @change="calculateColor" v-model="hue">
	<input type="range"  @change="calculateColor" v-model="saturation">
	<input type="range"  @change="calculateColor" v-model="lightness">
	<div :style="{background: currentColor}" class="current-color">&nbsp;</div>
  	<div class="color-patch-container">
		<div v-for="n in 12" class="color-patch" :style="{background: 'hsl('+ n*30 +', 100%, 50%)'}">
			&nbsp;
		</div>
	</div>
	<!-- YO {{calculateColor}} OY -->
  </div>
</template>

<script>
export default {
  name: 'colorpicker',
  data () {
    return {
      hue: 1,
      saturation: 1,
      lightness: 1,
      currentColor: this.calculateColor
    }
  },
  methods: {
  	calculateColor() {
  		console.log("this.hue", this.hue);
  		this.$emit("newColor",`hsl(${this.hue * 3.6}, ${this.saturation}%, ${this.lightness}%)`);
  		return `hsl(${this.hue * 3.6}, ${this.saturation}%, ${this.lightness}%)`;
  	},
  	setColor(hue) {
  		this.hue = hue;
  		this.saturation = 100;
  		this.lightness = 50;
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
}

.current-color {
	width: 100px;
	height: 100px;
}
.color-patch-container {
	display: grid;
	width: 50%;
	grid-template-columns: 1fr  1fr;
}

.color-patch {
	color: #fff;
	border: 5px solid #000;
}

.color-patch:hover {
	cursor: pointer;
}
</style>

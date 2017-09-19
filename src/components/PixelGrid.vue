<template>
  <div class="grid" @click="setPixelColor($event)" @mouseover="setPixelColor($event,'hover')">
    <div class="pixel" v-for="n in 1024" :id="'pixel-'+ n">&nbsp;</div>
  </div>
</template>
<!-- need to add total reset button, and eraser which sets individual pixels to default value
also export option with background or just sprites? or fill it entirely with diff color? -->
<script>
export default {
  name: 'pixelGrid',
  props: ["currentColor"],
  data () {
    return {
      
    }
  },
  methods: {
    setPixelColor(event, hover) {
      if (hover && event.which !== 1) {
        return;
      } else if(!event.target.matches("div.grid")) {
        console.log("here", event)
        event.target.style.background = this.currentColor;
      }
    }
  }
}

// have a function to read of all colors in grid to read out?
// maybe also add cut and paste functionality 
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .grid {
    user-select: none;
    height: 640px;
    /*width: 100%;*/
    width: 640px;
    margin-left: 5%;
    border: 1px solid #000;
/*    display: grid;
    grid-template-columns: 1% repeat(auto-fit);
    grid-template-rows: 1% repeat(auto-fit);*/
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;

  }
  .pixel {
    cursor: pointer;
    /*border: 1px solid #000;*/
    background: #d3d3d3;
    width: 20px;
    height: 20px;
/*    height: 5px;
    width: 5px;*/
  }

  .pixel:hover {
    background: rgba(128, 128, 128, 0.5);
  }
  /*just give more specificity, so once it has color wont get hover,a nd remove that class if they clear it*/
</style>

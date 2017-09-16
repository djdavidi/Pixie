<template>
  <div class="grid">
    <div class="pixel" v-for="n in 1024" :id="'pixel-'+ n"
      @click="setPixelColor($event)">&nbsp;</div>
  </div>
</template>

<script>
export default {
  name: 'pixelGrid',
  props: ["currentColor"],
  data () {
    return {
      
    }
  },
  methods: {
    setPixelColor(event) {
      // if(event.target.style.background !== original) {
      //   then set it to original
      // }
      // return ""
      console.log("event", event.currentTarget)
      event.target.style.background = this.currentColor;
      console.log("this", this.style)
      //    console.log("event", event.target)
      // event.arget.background='green'
      // console.log("this", this.style)
    }
  }
}

// mousedown- every hover push the element ids to array, 
// on mouseup, get unique and fill all of them
// also need on mousedown to trail it so hover would set it somehow?
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

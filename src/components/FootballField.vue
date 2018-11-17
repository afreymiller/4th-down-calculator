<template>
  <canvas id="football-field" width="480" height="216"></canvas>
</template>

<script>
import TeamCard from './TeamCard.vue'

export default {
  methods: {
    updateCanvas: function (){
      let canvas = document.getElementById('football-field')
      let ctx = canvas.getContext('2d')
      ctx.fillStyle = 'green'
      ctx.fillRect(0, 0, canvas.width, canvas.height)
      ctx.beginPath()
      ctx.arc(95, 50, 40, 0, 2 * Math.PI)
      ctx.stroke()
    }
  },
  mounted: function (){
    this.updateCanvas()
  }
}
</script>

<style lang="scss">
  #football-field {
    border: 1px solid #000000;
    // background-color: green;
  }
</style>
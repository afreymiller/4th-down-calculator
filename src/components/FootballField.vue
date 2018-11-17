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
      ctx.fillStyle = 'blue'
      ctx.fillRect(0, 0, 40, 216)
      ctx.fillRect(440, 0, 480, 216)
      ctx.strokeStyle='white'
      // #013220

      for (let i = 2; i < 23; i++) {
        ctx.beginPath()
        ctx.moveTo(20*i, 0)
        ctx.lineTo(20*i ,216)
        ctx.stroke()
      }
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
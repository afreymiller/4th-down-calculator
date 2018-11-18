<template>
  <canvas id="football-field" width="480" height="216"></canvas>
</template>

<script>
import TeamCard from './TeamCard.vue'

export default {
  props: {
    endzoneColor: {
      type: String,
      default: 'blue'
    }
  },
  methods: {
    updateCanvas: function (){
      let canvas = document.getElementById('football-field')
      let ctx = canvas.getContext('2d')
      ctx.fillStyle = 'green'
      ctx.fillRect(0, 0, canvas.width, canvas.height)
      ctx.fillStyle = this.endzoneColor
      ctx.fillRect(0, 0, 40, 216)
      ctx.fillRect(440, 0, 480, 216)
      ctx.fillStyle = '#006400'
      for (let i = 3; i < 23; i+=2) {
        ctx.fillRect(20*i, 0, 20, 216)
      }

      ctx.strokeStyle='white'

      for (let i = 2; i < 23; i++) {
        ctx.beginPath()
        ctx.moveTo(20*i, 0)
        ctx.lineTo(20*i ,216)
        ctx.stroke()
      }

      ctx.fillStyle = "white"
      ctx.font = "15px Arial"
      ctx.fillText('10',72,190)
      ctx.fillText('20',112,190)
      ctx.fillText('30',152,190)
      ctx.fillText('40',192,190)
      ctx.fillText('50',232,190)
      ctx.fillText('40',272,190)
      ctx.fillText('30',312,190)
      ctx.fillText('20',352,190)
      ctx.fillText('10',392,190)
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
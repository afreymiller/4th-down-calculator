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

      for (let i = 9; i < 88; i++) {
        ctx.beginPath()
        ctx.moveTo(5*i, 3)
        ctx.lineTo(5*i, 8)
        ctx.stroke()

        ctx.beginPath()
        ctx.moveTo(5*i, 75)
        ctx.lineTo(5*i, 80)
        ctx.stroke()

        ctx.beginPath()
        ctx.moveTo(5*i, 135)
        ctx.lineTo(5*i, 140)
        ctx.stroke()

        ctx.beginPath()
        ctx.moveTo(5*i, 207)
        ctx.lineTo(5*i, 212)
        ctx.stroke()
      }

      ctx.fillStyle = "white"
      ctx.font = "15px Arial"
      ctx.fillText('10',72,201)
      ctx.fillText('20',112,201)
      ctx.fillText('30',152,201)
      ctx.fillText('40',192,201)
      ctx.fillText('50',232,201)
      ctx.fillText('40',272,201)
      ctx.fillText('30',312,201)
      ctx.fillText('20',352,201)
      ctx.fillText('10',392,201)

      ctx.save()

      ctx.rotate(Math.PI)
      ctx.translate(-480,-72)
      ctx.fillText('10',72,55)
      ctx.fillText('20',112,55)
      ctx.fillText('30',152,55)
      ctx.fillText('40',192,55)
      ctx.fillText('50',232,55)
      ctx.fillText('40',272,55)
      ctx.fillText('30',312,55)
      ctx.fillText('20',352,55)
      ctx.fillText('10',392,55)

      ctx.restore()

      ctx.strokeStyle='yellow'
      ctx.beginPath()
      ctx.moveTo(60, 0)
      ctx.lineTo(60,216)
      ctx.stroke()

      ctx.strokeStyle='blue'
      ctx.beginPath()
      ctx.moveTo(85, 0)
      ctx.lineTo(85,216)
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
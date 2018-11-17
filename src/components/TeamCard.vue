<template>
  <div class="team-border row">
    <div class="col-4">
      <img 
        height="50px"
        width="50px"
        :src="srcPath"
      />
      <p>{{name}}</p>
    </div>
    <div class="col-2">
      <p>Other stats</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: ''
    }
  },
  // data () {
  //   return {
  //     srcPath: require('../assets/' + this.name + '.png')
  //   }
  // }
  computed: {
    srcPath: function () {
      return require('../assets/' + this.name + '.png')
    }
  }
}
</script>

<style lang="scss">
.team-border {
  border-style: dotted;
}
</style>
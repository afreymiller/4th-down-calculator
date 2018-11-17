<template>
  <div class="team-border row">
    <div class="col-3">
      <img 
        height="50px"
        width="50px"
        :src="srcPath"
      />
      <p>{{name}}</p>
    </div>
    <div class="col-1">
      <p>YPP:</p>
      <p>EP:</p>
    </div>
    <div class="col-3">
      <div class="progress">
        <div class="progress-bar" role="progressbar" aria-valuenow="70"
        aria-valuemin="0" aria-valuemax="100" style="width:70%">
          <span class="sr-only">70% Complete</span>
        </div>
      </div>
      <br>
      <div class="progress">
        <div class="progress-bar" role="progressbar" aria-valuenow="70"
        aria-valuemin="0" aria-valuemax="100" style="width:70%">
          <span class="sr-only">70% Complete</span>
        </div>
      </div>
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
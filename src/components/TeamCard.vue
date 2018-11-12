<template>
  <div>
    <img 
      height="100px"
      width="100px"
      :src="srcPath"
    />
    <p>{{name}}</p>
  </div>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: ''
    },
    path: {
      type: String,
      default: '../assets/CHI.png'
    }
  },
  data () {
    return {
      srcPath: require('../assets/' + this.name + '.png')
    }
  }
}
</script>
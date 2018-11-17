<template>
  <div>
    <img 
      height="50px"
      width="50px"
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
      default: 'CHI'
    }
  },
  data () {
    return {
      srcPath: require('../assets/' + this.name + '.png')
    }
  }
}
</script>
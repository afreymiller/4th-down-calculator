<template>
  <div id="app">
    <div class="jumbotron">
      <heading/>
      <div class="row">
        <div class="col">
          <team-card/>
        </div>
        <div class="col">
          <team-card/>
        </div>
        <div class="col">
          <team-card/>
        </div>
        <div class="col">
          <team-card/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Heading from './components/Heading.vue'
import TeamCard from './components/TeamCard.vue'

export default {
  name: 'app',
  components: {
    Heading,
    TeamCard
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>

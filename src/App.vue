<template>
  <div id="app">
    <div class="jumbotron">
      <heading/>
      <division
        v-for="division in divisions"
        :key="division.id"
        :teams="division.teams"
      />
    </div>
  </div>
</template>

<script>
import Division from './components/Division.vue'
import Heading from './components/Heading.vue'
import TeamCard from './components/TeamCard.vue'

export default {
  name: 'app',
  components: {
    Division,
    Heading,
    TeamCard
  },
  data () {
    return {
      divisions: [{
        id: 1,
        teams: [
          {name: 'Vikings'},
          {name: 'Bears'},
          {name: 'Lions'},
          {name: 'Packers'}
        ],
      },
      { 
        id: 2,
        teams: [
          {name: 'Vikings'},
          {name: 'Bears'},
          {name: 'Lions'},
          {name: 'Packers'}
        ]
      }]
    }
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

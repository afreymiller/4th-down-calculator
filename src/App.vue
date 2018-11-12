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
          {name: 'CHI'},
          {name: 'DET'},
          {name: 'GB'},
          {name: 'MIN'}
        ],
      },
      { 
        id: 2,
        teams: [
          {name: 'SF'},
          {name: 'ARI'},
          {name: 'LAR'},
          {name: 'SEA'}
        ]
      },
      {
        id: 3,
        teams: [
          {name: 'DAL'},
          {name: 'PHI'},
          {name: 'NYG'},
          {name: 'WAS'}
        ]
      },
      {
        id: 4,
        teams: [
          {name: 'TB'},
          {name: 'ATL'},
          {name: 'CAR'},
          {name: 'NO'}
        ]
      },
      {
        id: 5,
        teams: [
          {name: 'IND'},
          {name: 'TEN'},
          {name: 'JAX'},
          {name: 'HOU'}
        ],
      },
      { 
        id: 6,
        teams: [
          {name: 'NE'},
          {name: 'MIA'},
          {name: 'BUF'},
          {name: 'NYJ'}
        ]
      },
      {
        id: 7,
        teams: [
          {name: 'DEN'},
          {name: 'OAK'},
          {name: 'KC'},
          {name: 'LAC'}
        ]
      },
      {
        id: 8,
        teams: [
          {name: 'BAL'},
          {name: 'PIT'},
          {name: 'CLE'},
          {name: 'CIN'}
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

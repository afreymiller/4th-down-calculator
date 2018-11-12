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
          {name: 'Bears'},
          {name: 'Lions'},
          {name: 'Packers'},
          {name: 'Vikings'}
        ],
      },
      { 
        id: 2,
        teams: [
          {name: '49ers'},
          {name: 'Cardinals'},
          {name: 'Rams'},
          {name: 'Seahawks'}
        ]
      },
      {
        id: 3,
        teams: [
          {name: 'Cowboys'},
          {name: 'Eagles'},
          {name: 'Giants'},
          {name: 'Washington'}
        ]
      },
      {
        id: 4,
        teams: [
          {name: 'Buccaneers'},
          {name: 'Falcons'},
          {name: 'Panthers'},
          {name: 'Saints'}
        ]
      },
      {
        id: 5,
        teams: [
          {name: 'Bears'},
          {name: 'Lions'},
          {name: 'Packers'},
          {name: 'Vikings'}
        ],
      },
      { 
        id: 6,
        teams: [
          {name: '49ers'},
          {name: 'Cardinals'},
          {name: 'Rams'},
          {name: 'Seahawks'}
        ]
      },
      {
        id: 7,
        teams: [
          {name: 'Cowboys'},
          {name: 'Eagles'},
          {name: 'Giants'},
          {name: 'Washington'}
        ]
      },
      {
        id: 8,
        teams: [
          {name: 'Buccaneers'},
          {name: 'Falcons'},
          {name: 'Panthers'},
          {name: 'Saints'}
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

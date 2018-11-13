<template>
  <div id="app">
    <div class="container">
      <heading/>
      <division
        v-for="division in divisions"
        :key="division.id"
        :teams="division.teams"
      />
      <div class="row">
        <div class="col-3">
          <div class="form-group">
            <label for="home">Home Team:</label>
            <select v-model="homeSelected">
              <option 
                v-for="team in teamCodes"
                :key="team.name"
                :value="team.name"
              >
                {{ team.name }}
              </option>
            </select>
          </div>
        </div>
        <div class="col-3">
          <div class="form-group">
            <label for="away">Away Team:</label>
            <select v-model="awaySelected">
              <option 
                v-for="team in teamCodes"
                :key="team.name"
                :value="team.name"
              >
                {{ team.name }}
              </option>
            </select>
          </div>
        </div>
        <div class="col-3">
          <div class="form-group">
            <label for="yardLine">Position:</label>
            <select v-model="yardLine">
              <option 
                v-for="yard in yardLines"
                :key="yard.name"
                :value="yard.name"
              >
                {{ yard.name }}
              </option>
            </select>
          </div>
        </div>
        <div class="col-3">
          <div class="form-group">
            <label for="yardsToGo">Yards to Go:</label>
            <select v-model="yardsToGo">
              <option 
                v-for="yard in yards"
                :key="yard.name"
                :value="yard.value"
              >
                {{ yard.value }}
              </option>
            </select>
          </div>
        </div>
      </div>
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
      homeSelected: 'CHI',
      awaySelected: 'CHI',
      yardLine: 'Midfield',
      yardsToGo: '5',
      yards: [
        {name: '1', value: 1},
        {name: '2', value: 2},
        {name: '3', value: 3}, 
        {name: '4', value: 4},
        {name: '5', value: 5},
        {name: '6', value: 6},
        {name: '7', value: 7},
        {name: '8', value: 8},
        {name: '9', value: 9},
        {name: '10', value: 10},
        {name: '11', value: 11},
        {name: '12', value: 12},
        {name: '13', value: 13},
        {name: '14', value: 14},
        {name: '15', value: 15}
      ],
      yardLines: [
        {name: 'Own 1', toEndzone: 99},
        {name: 'Own 2', toEndzone: 98},
        {name: 'Own 3', toEndzone: 97},
        {name: 'Own 4', toEndzone: 96},
        {name: 'Own 5', toEndzone: 95},
        {name: 'Own 6', toEndzone: 94},
        {name: 'Own 7', toEndzone: 93},
        {name: 'Own 8', toEndzone: 92},
        {name: 'Own 9', toEndzone: 91},
        {name: 'Own 10', toEndzone: 90},
        {name: 'Own 11', toEndzone: 89},
        {name: 'Own 12', toEndzone: 88},
        {name: 'Own 13', toEndzone: 87},
        {name: 'Own 14', toEndzone: 86},
        {name: 'Own 15', toEndzone: 85},
        {name: 'Own 16', toEndzone: 84},
        {name: 'Own 17', toEndzone: 83},
        {name: 'Own 18', toEndzone: 82},
        {name: 'Own 19', toEndzone: 81},
        {name: 'Own 20', toEndzone: 80},
        {name: 'Own 21', toEndzone: 79},
        {name: 'Own 22', toEndzone: 78},
        {name: 'Own 23', toEndzone: 77},
        {name: 'Own 24', toEndzone: 76},
        {name: 'Own 25', toEndzone: 75},
        {name: 'Own 26', toEndzone: 74},
        {name: 'Own 27', toEndzone: 73},
        {name: 'Own 28', toEndzone: 72},
        {name: 'Own 29', toEndzone: 71},
        {name: 'Own 30', toEndzone: 70},
        {name: 'Own 31', toEndzone: 69},
        {name: 'Own 32', toEndzone: 68},
        {name: 'Own 33', toEndzone: 67},
        {name: 'Own 34', toEndzone: 66},
        {name: 'Own 35', toEndzone: 65},
        {name: 'Own 36', toEndzone: 64},
        {name: 'Own 37', toEndzone: 63},
        {name: 'Own 38', toEndzone: 62},
        {name: 'Own 39', toEndzone: 61},
        {name: 'Own 40', toEndzone: 60},
        {name: 'Own 41', toEndzone: 59},
        {name: 'Own 42', toEndzone: 58},
        {name: 'Own 43', toEndzone: 57},
        {name: 'Own 44', toEndzone: 56},
        {name: 'Own 45', toEndzone: 55},
        {name: 'Own 46', toEndzone: 54},
        {name: 'Own 47', toEndzone: 53},
        {name: 'Own 48', toEndzone: 52},
        {name: 'Own 49', toEndzone: 51},
        {name: 'Midfield', toEndzone: 50},
        {name: 'Opponent 49', toEndzone: 49},
        {name: 'Opponent 48', toEndzone: 48},
        {name: 'Opponent 47', toEndzone: 47},
        {name: 'Opponent 46', toEndzone: 46},
        {name: 'Opponent 45', toEndzone: 45},
        {name: 'Opponent 44', toEndzone: 44},
        {name: 'Opponent 43', toEndzone: 43},
        {name: 'Opponent 42', toEndzone: 42},
        {name: 'Opponent 41', toEndzone: 41},
        {name: 'Opponent 40', toEndzone: 40},
        {name: 'Opponent 39', toEndzone: 39},
        {name: 'Opponent 38', toEndzone: 38},
        {name: 'Opponent 37', toEndzone: 37},
        {name: 'Opponent 36', toEndzone: 36},
        {name: 'Opponent 35', toEndzone: 35},
        {name: 'Opponent 34', toEndzone: 34},
        {name: 'Opponent 33', toEndzone: 33},
        {name: 'Opponent 32', toEndzone: 32},
        {name: 'Opponent 31', toEndzone: 31},
        {name: 'Opponent 30', toEndzone: 30},
        {name: 'Opponent 29', toEndzone: 29},
        {name: 'Opponent 28', toEndzone: 28},
        {name: 'Opponent 27', toEndzone: 27},
        {name: 'Opponent 26', toEndzone: 26},
        {name: 'Opponent 25', toEndzone: 25},
        {name: 'Opponent 24', toEndzone: 24},
        {name: 'Opponent 23', toEndzone: 23},
        {name: 'Opponent 22', toEndzone: 22},
        {name: 'Opponent 21', toEndzone: 21},
        {name: 'Opponent 20', toEndzone: 20},
        {name: 'Opponent 19', toEndzone: 19},
        {name: 'Opponent 18', toEndzone: 18},
        {name: 'Opponent 17', toEndzone: 17},
        {name: 'Opponent 16', toEndzone: 16},
        {name: 'Opponent 15', toEndzone: 15},
        {name: 'Opponent 14', toEndzone: 14},
        {name: 'Opponent 13', toEndzone: 13},
        {name: 'Opponent 12', toEndzone: 12},
        {name: 'Opponent 11', toEndzone: 11},
        {name: 'Opponent 10', toEndzone: 10},
        {name: 'Opponent 9', toEndzone: 9},
        {name: 'Opponent 8', toEndzone: 8},
        {name: 'Opponent 7', toEndzone: 7},
        {name: 'Opponent 6', toEndzone: 6},
        {name: 'Opponent 5', toEndzone: 5},
        {name: 'Opponent 4', toEndzone: 4},
        {name: 'Opponent 3', toEndzone: 3},
        {name: 'Opponent 2', toEndzone: 2},
        {name: 'Opponent 1', toEndzone: 1}
      ],
      /* There shouldn't be a need for both team codes and divisions */
      teamCodes: [
        {name: 'CHI'},
        {name: 'DET'},
        {name: 'GB'},
        {name: 'MIN'},
        {name: 'SF'},
        {name: 'ARI'},
        {name: 'LAR'},
        {name: 'SEA'},
        {name: 'DAL'},
        {name: 'PHI'},
        {name: 'NYG'},
        {name: 'WAS'},
        {name: 'TB'},
        {name: 'ATL'},
        {name: 'CAR'},
        {name: 'NO'},
        {name: 'IND'},
        {name: 'TEN'},
        {name: 'JAX'},
        {name: 'HOU'},
        {name: 'NE'},
        {name: 'MIA'},
        {name: 'BUF'},
        {name: 'NYJ'},
        {name: 'DEN'},
        {name: 'OAK'},
        {name: 'KC'},
        {name: 'LAC'},
        {name: 'BAL'},
        {name: 'PIT'},
        {name: 'CLE'},
        {name: 'CIN'}
      ],
      divisions: [{
        id: 1,
        teams: [
          {name: 'ARI'},
          {
            name: 'ATL', 
            expP: [{1: -1.3, 2: -0.8, 3: 1.2, 4: 1.7, 5: 2.1, 6: 2.5, 7: 2.7, 8: 2.9, 9: 3.2, 10: 4.0}]},
          {
            name: 'BAL'
          },
          {name: 'BUF'},
          {name: 'CAR'},
          {name: 'CHI'},
          {name: 'CIN'},
          {name: 'CLE'}
        ],
      },
      {
        id: 2,
        teams: [
          {name: 'DAL'},
          {name: 'DEN'},
          {name: 'DET'},
          {name: 'GB'},
          {name: 'HOU'},
          {name: 'IND'},
          {name: 'JAX'},
          {name: 'KC'}
        ]
      },
      {
        id: 3,
        teams: [
          {name: 'LAC'},
          {name: 'LAR'},
          {name: 'MIA'},
          {name: 'MIN'},
          {name: 'NE'},
          {name: 'NO'},
          {name: 'NYG'},
          {name: 'NYJ'}
        ],
      },
      { 
        id: 4,
        teams: [
          {name: 'OAK'},
          {name: 'PHI'},
          {name: 'PIT'},
          {name: 'SEA'},
          {name: 'SF'},
          {name: 'TB'},
          {name: 'TEN'},
          {name: 'WAS'}
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

<template>
  <div id="app">
    <div class="container">
      <heading/>
      <!-- TODO: Make this its own component -->
      <football-field/>
      <div class="row">
        <div class="col-6">
          <team-card
            :name="offenseSelected"
          />
        </div>
        <div class="col-6">
          <team-card
            :name="defenseSelected"
          />
        </div>
      </div>
      <!-- TODO: This whole row should be a component, probably several -->
      <div class="row justify-content-center">
        <div class="col-2">
          <div class="form-group">
            <label for="home">Offense:</label>
            <select v-model="offenseSelected">
              <option 
                v-for="team in teams"
                :key="team.name"
                :value="team.name"
              >
                {{ team.name }}
              </option>
            </select>
          </div>
        </div>
        <div class="col-2">
          <div class="form-group">
            <label for="away">Defense:</label>
            <select v-model="defenseSelected">
              <option 
                v-for="team in teams"
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
        <div class="col-2">
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
      <!-- TODO: This should be its own component -->
      <p>1st Down Conversion Probability: {{ probabilityConversionDisplay }}</p>
      <p>Conversion Expectation + Failure Expectation = {{ convertExpectationDisplay }} + {{ failureExpectationDisplay }}</p>
      <p> = {{ totalExpectationDisplay }} </p>
      <p
        :class="messageColor"
      >
        {{ message }}
      </p>
    </div>
  </div>
</template>

<script>
import FootballField from './components/FootballField.vue'
import Heading from './components/Heading.vue'
import TeamCard from './components/TeamCard.vue'
import TeamRow from './components/TeamRow.vue'

export default {
  name: 'app',
  components: {
    FootballField,
    Heading,
    TeamCard,
    TeamRow
  },
  data () {
    return {
      offenseSelected: 'CHI',
      defenseSelected: 'MIN',
      yardLine: 'Midfield',
      yardsToGo: 11,
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
        {name: '15+', value: 15}
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
      teams: [
        {
          name: 'ARI',
          division: 1,
          offYPP: 5.4,
          defYPP: 4.8, 
          offEP: {10: -1.2, 9: -0.7, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.2, 2: -0.1, 3: -0.4, 4: -1.0, 5: -1.2, 6: -1.7, 7: -2.0, 8: -2.5, 9: -2.9, 10: -3.3}
        },
        {
          name: 'ATL',
          division: 1,
          offYPP: 6.7,
          defYPP: 5.6, 
          offEP: {10: -1.3, 9: -0.9, 8: 1.1, 7: 1.5, 6: 1.8, 5: 2.3, 4: 2.5, 3: 3.1, 2: 3.3, 1: 3.6},
          defEP: {1: 1.3, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'BAL',
          division: 1,
          offYPP: 5.2,
          defYPP: 5.2,
          offEP: {10: -1.5, 9: -0.8, 8: 1.1, 7: 1.4, 6: 1.8, 5: 2.2, 4: 2.5, 3: 2.7, 2: 3.0, 1: 3.5},
          defEP: {1: 1.4, 2: -0.3, 3: -0.5, 4: -0.8, 5: -1.0, 6: -1.3, 7: -1.6, 8: -2.0, 9: -2.4, 10: -2.7}
        },
        {
          name: 'BUF',
          division: 1,
          offYPP: 5.6,
          defYPP: 5.6,
          offEP: {10: -1.5, 9: -0.8, 8: 1.1, 7: 1.4, 6: 1.8, 5: 2.2, 4: 2.5, 3: 2.7, 2: 3.0, 1: 3.5},
          defEP: {1: 1.4, 2: -0.3, 3: -0.5, 4: -0.8, 5: -1.0, 6: -1.3, 7: -1.6, 8: -2.0, 9: -2.4, 10: -2.7}
        },
        {
          name: 'CAR',
          division: 1,
          offYPP: 5.2,
          defYPP: 5.6,
          offEP: {10: -1.5, 9: -0.8, 8: 1.1, 7: 1.4, 6: 1.8, 5: 2.2, 4: 2.5, 3: 2.7, 2: 3.0, 1: 3.5},
          defEP: {1: 1.4, 2: -0.3, 3: -0.5, 4: -0.8, 5: -1.0, 6: -1.3, 7: -1.6, 8: -2.0, 9: -2.4, 10: -2.7}
        },
        {
          name: 'CHI',
          division: 1,
          offYPP: 5.9,
          defYPP: 5.5,
          offEP: {10: -1.5, 9: -0.8, 8: 1.1, 7: 1.4, 6: 1.8, 5: 2.2, 4: 2.5, 3: 2.7, 2: 3.0, 1: 3.5},
          defEP: {1: 1.4, 2: -0.3, 3: -0.5, 4: -0.8, 5: -1.0, 6: -1.3, 7: -1.6, 8: -2.0, 9: -2.4, 10: -2.7}
        },
        {
          name: 'CIN',
          division: 1,
          offYPP: 5.4,
          defYPP: 5.4,
          offEP: {10: -1.5, 9: -0.8, 8: 1.1, 7: 1.4, 6: 1.8, 5: 2.2, 4: 2.5, 3: 2.7, 2: 3.0, 1: 3.5},
          defEP: {1: 1.4, 2: -0.3, 3: -0.5, 4: -0.8, 5: -1.0, 6: -1.3, 7: -1.6, 8: -2.0, 9: -2.4, 10: -2.7}
        },
        {
          name: 'CLE',
          division: 1,
          offYPP: 5.1,
          defYPP: 5.9,
          offEP: {10: -1.5, 9: -0.8, 8: 1.1, 7: 1.4, 6: 1.8, 5: 2.2, 4: 2.5, 3: 2.7, 2: 3.0, 1: 3.5},
          defEP: {1: 1.4, 2: -0.3, 3: -0.5, 4: -0.8, 5: -1.0, 6: -1.3, 7: -1.6, 8: -2.0, 9: -2.4, 10: -2.7}
        },
        {
          name: 'DAL',
          division: 2,
          offYPP: 6.0,
          defYPP: 5.5,
          offEP: {10: -1.5, 9: -0.8, 8: 1.1, 7: 1.4, 6: 1.8, 5: 2.2, 4: 2.5, 3: 2.7, 2: 3.0, 1: 3.5},
          defEP: {1: 1.4, 2: -0.3, 3: -0.5, 4: -0.8, 5: -1.0, 6: -1.3, 7: -1.6, 8: -2.0, 9: -2.4, 10: -2.7}
        },
        {
          name: 'DEN',
          division: 2,
          offYPP: 5.1,
          defYPP: 4.7,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'DET',
          division: 2,
          offYPP: 5.5,
          defYPP: 5.9,
          offEP: {10: -1.3, 9: -0.9, 8: 1.1, 7: 1.5, 6: 1.8, 5: 2.3, 4: 2.5, 3: 3.1, 2: 3.3, 1: 3.6},
          defEP: {1: 1.3, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'GB',
          division: 2,
          offYPP: 5.7,
          defYPP: 5.9,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'HOU',
          division: 2,
          offYPP: 4.7,
          defYPP: 5.1,
          offEP: {10: -1.3, 9: -0.9, 8: 1.1, 7: 1.5, 6: 1.8, 5: 2.3, 4: 2.5, 3: 3.1, 2: 3.3, 1: 3.6},
          defEP: {1: 1.3, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'IND',
          division: 2,
          offYPP: 5.6,
          defYPP: 6.0,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'JAX',
          division: 2,
          offYPP: 5.1,
          defYPP: 5.0,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'KC',
          division: 2,
          offYPP: 5.5,
          defYPP: 5.5,
          offEP: {10: -1.3, 9: -0.9, 8: 1.1, 7: 1.5, 6: 1.8, 5: 2.3, 4: 2.5, 3: 3.1, 2: 3.3, 1: 3.6},
          defEP: {1: 1.3, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'LAC',
          division: 3,
          offYPP: 5.6,
          defYPP: 5.4,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 0.5, 2: -0.1, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'LAR',
          division: 3,
          offYPP: 4.4,
          defYPP: 5.2,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'MIA',
          division: 3,
          offYPP: 5.8,
          defYPP: 5.6,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'MIN',
          division: 3,
          offYPP: 5.0,
          defYPP: 5.1,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'NE',
          division: 3,
          offYPP: 5.9,
          defYPP: 5.2,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'NO',
          division: 3,
          offYPP: 6.2,
          defYPP: 6.0,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'NYG',
          division: 3,
          offYPP: 5.2,
          defYPP: 5.1,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'NYJ',
          division: 3,
          offYPP: 5.3,
          defYPP: 5.5,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'OAK',
          division: 4,
          offYPP: 5.7,
          defYPP: 6.1,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'PHI',
          division: 4,
          offYPP: 5.0,
          defYPP: 5.6,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'PIT',
          division: 4,
          offYPP: 5.8,
          defYPP: 5.5,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'SEA',
          division: 4,
          offYPP: 5.6,
          defYPP: 5.0,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'SF',
          division: 4,
          offYPP: 4.9,
          defYPP: 5.9,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'TB',
          division: 4,
          offYPP: 5.4,
          defYPP: 6.0,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'TEN',
          division: 4,
          offYPP: 5.7,
          defYPP: 5.5,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        },
        {
          name: 'WAS',
          division: 4,
          offYPP: 6.4,
          defYPP: 5.8,
          offEP: {10: -1.3, 9: -0.8, 8: 1.2, 7: 1.7, 6: 2.1, 5: 2.5, 4: 2.7, 3: 2.9, 2: 3.2, 1: 4.0},
          defEP: {1: 1.4, 2: -0.2, 3: -0.3, 4: -1.1, 5: -1.4, 6: -1.6, 7: -1.9, 8: -2.6, 9: -2.8, 10: -3.4}
        }
      ]
    }
  },
  computed: {
    probabilityOfConversion: function () {
      let [offense] = this.teams.filter(e => e.name === this.offenseSelected)
      let [defense] = this.teams.filter(e => e.name === this.defenseSelected)

      /* TODO: Get rid of this */
      const LEAGUE_AVERAGE = 5.49

      let lambda = (offense.offYPP * defense.defYPP) / LEAGUE_AVERAGE
      return this.getPoissonRightTail(lambda, this.yardsToGo)
    },
    convertExpectation: function () {
      return this.probabilityOfConversion * this.ifConversionGetOffensiveEP(true)
    },
    failureExpectation: function () {
      return (1 - this.probabilityOfConversion) * this.ifConversionGetOffensiveEP(false)
    },
    totalExpectation: function () {
      return this.convertExpectation + this.failureExpectation
    },
    messageColor: function () {
      if (this.totalExpectation < 0) {
        return 'error'
      }
      if (this.totalExpectation < 0.3) {
        return 'warning'
      }
      return 'success'
    },
    totalExpectationDisplay: function () {
      return parseFloat(this.totalExpectation).toFixed(2)
    },
    probabilityConversionDisplay: function () {
      return parseFloat(this.probabilityOfConversion).toFixed(2)
    },
    convertExpectationDisplay: function () {
      return parseFloat(this.convertExpectation).toFixed(2)
    },
    failureExpectationDisplay: function () {
      return parseFloat(this.failureExpectation).toFixed(2)
    },
    message: function () {
      if (this.totalExpectation < 0) {
        return 'You should probably punt.'
      }
      if (this.totalExpectation < 0.3) {
        return 'Tread lightly.'
      }
      return 'Fortune favors the bold, go for it!'
    }
  },
  
  methods: {
    factorial (n) {
      let result = 1

      while (n > 0) {
        result *= n
        n--
      }

      return result
    },
    ifConversionGetOffensiveEP (worked) {
      if (worked) {
        let [currYard] = this.yardLines.filter(e => e.name === this.yardLine)
        let newYardage = currYard.toEndzone - this.yardsToGo
        let newBucket = Math.ceil(newYardage/10)

        let [offense] = this.teams.filter(e => e.name === this.offenseSelected)
        return offense.offEP[newBucket]
      } else {
        let [currYard] = this.yardLines.filter(e => e.name === this.yardLine)
        let newBucket = Math.ceil(currYard.toEndzone/10)

        let [offense] = this.teams.filter(e => e.name === this.offenseSelected)
        return offense.defEP[newBucket]
      }
    },
    getDiscretePoisson (lambda, k) {
      return (Math.pow(Math.E, -lambda) * Math.pow(lambda, k)) / this.factorial(k)
    },
    getPoissonRightTail (lambda, k) {
      let mass = 0
      k--

      while (k >= 0) {
        mass += this.getDiscretePoisson(lambda, k)
        k--
      }

      return 1 - mass
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

.error {
  color: red;
}

.success {
  color: green;
}

.warning {
  color: orange;
}

a {
  color: #42b983;
}
</style>

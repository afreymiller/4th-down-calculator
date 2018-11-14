<template>
  <div class="row">
    <div class="col"
      v-for="team in teams"
      :key="team.name"
    >
      <team-card
      :name="team.name"
      />
    </div>
  </div>
</template>

<script>
import TeamCard from './TeamCard.vue'

export default {
  components: {
    TeamCard
  },
  props: {
    teams: {
      type: Array,
      default: []
    }
  }
}
</script>
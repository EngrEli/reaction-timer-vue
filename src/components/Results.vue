<template>
  <div class="results">
    <div>
      Reaction Time - {{ reactionTimerResults }} seconds
    </div>
    <h2>{{ getResultsText() }}</h2>
  </div>
  
</template>

<script>
export default {
  name: 'Results',
  props: {
    reactionTimerResults: Number
  },
  methods: {
    getResultsText() {
      if (this.reactionTimerResults < 1) {
        return "Fast Reflex!"
      } else if (this.reactionTimerResults < 4) {
        return "Slooooow"
      } else if (this.reactionTimerResults >= 5) {
        return "Snail Pace..."
      }
    }
  },
  updated() {
    alert('tite')
  }
}
</script>

<style scoped>
.results {
  margin-top: 20px;
}
</style>
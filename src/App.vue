<template>
  <h1>Reaction Timer</h1>
  <button @click="startGame" class="btn btn--play" :disabled="isPlaying">
    {{ hasPlayed ? "Play again": "Play" }}
  </button>
  <Block v-if="isPlaying" @end="handleEndGame"/>  
  <Results v-if="isResultsShown" :reactionTimerResults="parseFloat(reactionTimerResults)" />
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  data() {
    return {
      isPlaying: false,
      reactionTimerResults: null,
      isResultsShown: false,
      hasPlayed: false,
    }
  },
  components: {
    Block,
    Results,
  },
  methods: {
    startGame() {
      setTimeout(() => {
        this.isPlaying = true
      }, (Math.random() * 6) * 1000);
      this.isResultsShown = false
    },
    handleEndGame(reactionTimer) {
      this.reactionTimerResults = reactionTimer;
      this.isPlaying = false
      this.isResultsShown = true
      this.hasPlayed = true
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;700&display=swap');

#app {
  font-family: 'Montserrat', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.btn {
  padding: 10px 15px;
  border: 0;
  border-radius: 5px;
}

.btn--play {
  background: #039C88;
  color: #FFFFFF;
  cursor: pointer;
}

.btn--play:disabled {
  background: #879d9a;
  cursor: not-allowed;
}

.btn--play:hover {
  filter: brightness(0.8);
}

</style>

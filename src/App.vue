<template>
  <h1>Reaction Timer</h1>
  <button @click="startGame" class="btn btn--play" :disabled="isPlaying">Play</button>
  <Block v-if="isBlockShown" @handleClickBlock="clickBlock" />
  <Results 
    v-if="isResultsShown"
    :resultsText="resultsText"
    :seconds="seconds"
  />
  <h1>{{ resultsText }}</h1>
</template>

<script>
// 1. Style play button - DONE
// 2. Clicking play displays block component but with a delay DONE
// 3. Clicking block component calculates the speed it was clicked after it was displayed.
// 4. (EXTRA) Create extra component for buttons like play
// 5. Add extra data to keep track if the player is currently playing the game

import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  data() {
    return {
      isPlaying: false,
      isBlockShown: false,
      isBlockClicked: false,
      isResultsShown: false,
      seconds: null,
      resultsText: '',
    }
  },
  components: {
    Block,
    Results,
  },
  methods: {
    startGame() {
      // Generate random number
      setTimeout(() => {
        this.isBlockShown = true
        this.isPlaying = true
        console.log(this.isBlockShown);

        // Fix error dito
        let startTime = Date.now();
        let timesRun = 0;
        let seconds = setInterval(() => {
            var elapsedTime = Date.now() - startTime;
            console.log((elapsedTime / 1000).toFixed(3));
            this.seconds = (elapsedTime / 1000).toFixed(3);

            timesRun += 1;
            if(timesRun === 80){
                clearInterval(seconds);
            }
        }, 100);
      }, (Math.floor(Math.random() * 6)) * 1000);
    },
    clickBlock() {
      this.isBlockClicked = true
      this.isResultsShown = true
      alert(this.seconds);
      if (this.seconds < 1) {
        this.resultsText = "Fast Reflex!"
      } else if (this.seconds < 4) {
        this.resultsText = "Slooooow"
      } else if (this.seconds >= 5) {
        this.resultsText = "Snail Pace..."
      }
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

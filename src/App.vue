<template>
  <h1>Hassan's Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
  <ResultsIn v-if="showResults" :score="score"></ResultsIn>
</template>

<script>

import Block from './components/BlockOne.vue';
import ResultsIn from './components/ResultsIn.vue'
export default {

  name: 'App',
  components: { Block, ResultsIn },
  data() {
    return {
      isPlaying: false,
      showResults: false,
      delay: null,
      score: null,
    }
  },

  methods: {
    start() {
      this.delay = 2000 + Math.random() * 1000
      this.isPlaying = true
      this.showResults = false
    },

    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true

    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

button {
  background-color: rgb(11, 105, 73);
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>

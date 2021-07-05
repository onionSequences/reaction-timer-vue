<template>
  <h1>Reaction timer ⏱️</h1>
  <Instruction v-if="showInstuctions" @close="closeModal" />
  <button @click="start" :disabled="isPlaying">Play</button>
  <button class="instruction-btn" @click="openModal">HOW TO PLAY</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score"/>
</template>

<script>
import Instruction from './components/Instruction.vue'
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Instruction,
    Block,
    Results
  },
  data() {
    return {
      isPlaying: false,
      showInstuctions: true,
      delay: null,
      score: null,
      showResults: false
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 3000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    },
    closeModal() {
      this.showInstuctions = false
    },
    openModal() {
      this.showInstuctions = true
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
  color: #2c3e50;
  margin-top: 60px;
}

button {
  background: #26c09e;
  border: none;
  padding: 10px 20px;
  text-transform: uppercase;
  font-weight: bold;
  cursor: pointer;
  color: #fff;
}

button:disabled {
  background: #a3a3a3;
  cursor: not-allowed;
}

.instruction-btn {
  background-color: #cfcece;
  color: #fff;
  margin-left: 15px;

}
</style>

<template>
  <h2>Ninja Reaction Timer</h2>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="score" :score="score" />
</template>

<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue';

export default {
  name: 'App',
  components: {
    Block,
    Results,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
    };
  },
  methods: {
    start() {
      this.score = null;
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      console.log(this.delay);
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #1695a3;
  margin-top: 60px;
}
button {
  background-color: #0faf87;
  color: white;
  border: none;
  padding: 5px 10px;
  font-size: 0.9em;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>

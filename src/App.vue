<template>
  <h2>Ninja Reaction Timer</h2>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <p v-if="score">Reaction Time: {{ score }} ms</p>
</template>

<script>
import Block from './components/Block.vue';

export default {
  name: 'App',
  components: {
    Block,
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
</style>

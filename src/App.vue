<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Start</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"></Block>
  <!-- <p v-if="showResult">reactionTime:{{ score }} ms</p> -->
  <Result v-if="showResult" :score="score"/>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Block from "./components/Block.vue";
import Result from "./components/Result.vue"
export default {
  name: "App",
  components: {
    Block,
    Result
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  methods: {
    start() {
      console.log("Hello");
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResult=false
      console.log("delay", this.delay);
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      console.log("reactTime", reactionTime);
      this.isPlaying = false;
      this.showResult = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Impact, 'Arial Narrow Bold', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

button{
  border-radius: 20px;
  padding: 8px 16px;
  background-color: #2c3e50;
  color: beige;
  font-size: 16px;
  border: none;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>

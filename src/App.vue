<template>
  <h2>Reaction Timer Game</h2>
  <button
    @click="start"
    :disabled="isPlaying"
    v-bind:class="{ disabled: isPlaying }"
  >
    Play
  </button>
  <Blog v-if="isPlaying" :delay="delay" @end="endgame" />
  <Results :score="score" v-if="showResults" />
</template>

<script>
import Blog from "./components/Blog.vue";
import Results from "./components/Results.vue"
export default {
  components: {
    Blog,Results,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score:null,
      showResults:false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults=false;
    },
    endgame(reactionTime){
       this.score = reactionTime;
       this.isPlaying=false;
       this.showResults=true;
    }
  },

};
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
  padding: 15px;
  font-size: 20px;
  width: 150px;
  border-radius: 5px;
  background: coral;
  color: azure;
  margin-bottom: 15px;
}

.disabled {
  background: darkgray;
}
</style>

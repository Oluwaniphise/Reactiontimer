<template>
 <h1>Ninja Reaction Timer</h1>

<button @click="start" :disabled="isPlaying">Play</button>

<TimerBlock  v-if="isPlaying" :delay="delay" @end="endGame" />
<TimerResult  v-if="showResults" :score="score" />
<!-- <p>score: {{score}} ms</p> -->
</template>
 

<script>
import TimerBlock from './components/TimerBlock.vue'
import TimerResult from './components/TimerResult.vue'


export default {
  name: 'App',
  data(){
    return {
      isPlaying:false,
      delay: null,
      score:null,
      showResults:false
    }
  },
  components: {TimerBlock, TimerResult},
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false

     
    },
    endGame(reactionTime){
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
</style>

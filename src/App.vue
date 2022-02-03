<template>
  <div>
    <h1>Reaction Time v2</h1>
    <button class="button-play" :disabled="play" @click="start">play</button>
    <Block v-if="play" @end="unPlay" :delay="delay" />
    <Result v-if="showResult" :time="timeResult"/>
  </div>
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";
export default {
  name: 'App',
  data(){
    return({
      play : false,
      delay : null,
      timeResult : null,
      showResult : false
    })
  },
  methods : {
    start(){
      this.showResult = false;
      this.end = false;
      this.delay = 2000 + Math.random() * 5000;
      this.play = true;
    },
    unPlay(reactionTime){
      this.timeResult = reactionTime;
      this.play = false;
      this.end = true;
      this.showResult = true;
    }
  },
  components:{
    'Block' : Block,
    'Result' : Result,
  }
}
</script>

<style>
#app {
  font-family: 'Open Sans', sans-serif;
  text-align: center;
  color: #283593;
  margin-top: 60px;
}
#app h1{
  color: #504539;
}
.button-play{
  border: 0px;
  background-color: #3F51B5;
  color: #E8EAF6;
  padding: 7px 20px;
  margin-bottom: 10px;
  border-radius: 5px;
}
.button-play:disabled{
  background-color: #7986CB;
}

.button-play:hover:enabled{
  background-color: #1A237E;
}
</style>

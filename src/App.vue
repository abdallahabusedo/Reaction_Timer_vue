<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div class="header">
      <h1>Welcome to Posidoon Reaction Timer :D</h1>
      <button @click="testClick" class="btnt" :disabled="isPlayeing">Test your reaction</button>
  </div>
  <Results v-if="showBtn" :score="this.score" />
  <Reactions v-if="isPlayeing" :delay="delay" @end="endGame"  />
</template>

<script>
import Reactions from "./components/Reactions.vue"
import Results from "./components/Results.vue";
export default {
  name: 'App',
  data(){
    return {
      isPlayeing : false,
      delay : null,
      score : null, 
      showBtn : false,
    }
  },
  components: {
    Reactions,
    Results
},
  methods :{
        testClick(){ 
            this.isPlayeing = true;
            this.delay = 2000 + Math.random() * 5000;
            setTimeout(() => { console.log("delay " + this.delay/1000 + " seconds" ); }, this.delay)
            this.showBtn = false
        },
        endGame(reactiontimer){
          this.score = reactiontimer
          this.isPlayeing = false
          this.showBtn =true
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
 .header{
        align-content: center; 
        align-self: center;
    }
    .btnt {
        width: 30%;
        height: 50px;
        background: rgb(93, 172, 93);
        border: 1px crimson;
        border-radius: 15px;
        color : white;
        font-size: 20px;
        max-width: 200px;
    }
</style>

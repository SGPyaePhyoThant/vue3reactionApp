<template>
<h3>こんにちは、リエションタイムです。</h3>
<button @click="start" :disabled="isPlaying">プレイ</button>
<Block v-if="isPlaying" :delay="delay" @stopByBlockComponent="showReactionTimer" @showMattePara="showMatte"/>
<Results v-if="showClickedTime">
  <template v-slot:resultValue>
    <h3>全部は{{clickedTime}}MiliSecond</h3>
    <h3>{{rank}}</h3>
  </template>
</Results>
<p v-show="showMatteParagraph" >ちょっと待ってね。。いまタイマーが数えているんだよ。</p>
<!-- <p v-if="showClickedTime">全部は{{clickedTime}}ms</p> -->
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data(){
    return {
      isPlaying:false,
      delay:null,
      clickedTime:null,
      showClickedTime:false,
      showMatteParagraph:false,
      rank:null
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying =true
      this.showClickedTime = false
  },
  showReactionTimer(reactionTimer){
    this.clickedTime = reactionTimer
    this.isPlaying = false
    this.showClickedTime = true
    this.showMatteParagraph = false
    if(reactionTimer<250){
     this.rank = ' ランクはニンジャです。'
    } else if(reactionTimer < 500){
      this.rank ='早いけど。。。'
    }else{
     this.rank = '頑張ってね。。。'
    }
  },
  showMatte(){
    this.showMatteParagraph = true
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

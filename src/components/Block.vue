
<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    クリックしてタイマーが終わる。
  </div>
</template>

<script>
export default {
    data(){
        return {
            showBlock:false,
            timer:null,
            reactionTime:0
        }
    },
props:['delay'],
mounted(){
    setTimeout(()=>{
        this.showBlock = true
        this.startTimer()
    },this.delay)
},
updated(){
    // console.log('3')
},
unmounted(){
    // console.log('this is unmounted state')
},
methods:{
    startTimer(){
        this.$emit('showMattePara')
        this.timer = setInterval(()=>{
            this.reactionTime += 10
            console.log('________reactionTimer____________',this.reactionTime)
        },10)
    },
    stopTimer(){
        console.log('________this.timer________',this.timer)
        clearInterval(this.timer)
        this.$emit('stopByBlockComponent',this.reactionTime)
    }
}
}
</script>

<style scoped>
.block{
    width: 400px;
    border-radius:20px;
    background:#0faf87;
    color: #fff;
    text-align:center;
    padding:100px 0;
    margin: 40px auto; 
}
</style>
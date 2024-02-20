
<template>
  <div class="block" v-if="showBlock">
    Click
  </div>
</template>

<script>
export default {
    data(){
        return {
            showBlock:false
        }
    },
props:['delay'],
mounted(){
    console.log('component mounted')
    setTimeout(()=>{
        this.showBlock = true
        console.log('this.showBloc after Delay', this.delay)
        console.log('1')
    },this.delay)
        console.log('2')
},
updated(){
    console.log('3')
},
unmounted(){
    console.log('this is unmounted state')
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
<template>
<div class="box">
<h3 >結果はこちら！</h3>
  <slot name="resultValue"> 
  </slot>
</div>
  
</template>

<script>
export default {

}
</script>

<style>
.box{
    width: 400px;
  padding: 20px;
  margin: 100px auto;
  background: #a70000;
  color: #ffc400;
  border-radius: 10px;
}
</style>

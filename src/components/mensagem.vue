<template>
 <div class="mensage-container">
 <p>{{ msg }}</p>
 </div>
</template>
<script>
export default{
  name:"mensage",
  props:{
    msg:String 
  }

}


</script>
<style scoped>
 .mensage-container{
  color: rgb(98, 97, 97);
  background-color: #fbf0b1;
  border: 2px solid #968834;
  border-radius: 15px;
  padding: 10px;
  max-width: 400px;
  margin: 30px auto;
  transition: 2s;
 }

@keyframes AnimatedMensagem {
  to{

  }
}
</style>
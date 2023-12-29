<template>

   <div id="main-banner">
     <h1>Make your burguer</h1>
   </div>

</template>
<script>
export default{
   name:"Banner",
}

</script>

<style scoped>
 #main-banner {
      background-image: url('/img/burger.jpg');
       height: 500px; 
       background-position: center; 
      background-repeat: no-repeat; 
      background-size: cover; 
       display: flex;
      align-items: center;
      justify-content: flex-start;
  }
  #main-banner h1{
   color: white;
   text-align: center;
   font-size: 60px;
   background-color: #444444;
   padding: 20px 40px;
   border-top: 2px solid ;
   border-right:2px solid ;
  }



</style>
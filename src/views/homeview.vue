
<template>
<div>
 <Banner/>
<div class="main-container">
<h1>Home</h1>
<burgerForm/>
</div>

</div>
</template>
<script>
import Banner from '../components/banner.vue';
import burgerForm from '../components/burgerform.vue';
export default {
   name:'Home',
   components:{
      Banner,
      burgerForm,
   }
}
</script>
<style>
</style>

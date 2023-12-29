
<template>
  <header>
    <div id="app">
        <NavBar :logo="logo_src" :alt="app_name"/>
        <RouterView />
    <Footer />
        
    </div>
  </header>


</template>
<script>
import NavBar from './components/navbar.vue';
import Footer from './components/footer.vue';
export default{
  name:"App",
  components:{
    NavBar,
    Footer
  },
  data(){
    return{
      logo_src:"/img/logo.png",
      app_name:'Make your burguer'
    }
  }
}
</script>
<style>
*{
  font-family: Helvetica, sans-serif;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
.main-container{
  margin: 50px;
  min-height: 480px
}
h1{
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}
</style>

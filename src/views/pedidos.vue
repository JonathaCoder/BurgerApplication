<template>
  <div class="main-container">
    
    <h1>Pedidos</h1>
  
    <Dashboard />
    
  </div>
</template>
<script>

import Dashboard from '../components/Dashboard.vue'

export default{
    name: "pedidos",

    components:{
    Dashboard,
  
},

}
</script>
<style scoped>

h1{
  background-color: #ffd560;
  border-radius: 5px;
  border: 1px solid;
  padding: 20px;
}

</style>


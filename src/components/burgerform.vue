<template>
   <div>
   <mensage :msg="msg" v-show="msg"/>
     <div>
      <form id="burger-form" @submit="createBurger">
           <div class="input_container">
            <label for="nome">Client Name </label>
            <input type="text" id="nome" name="nome" v-model="nome" placeholder="digite seu nome">
           </div>
           <div class="input_container">
            <label for="pao"> Choice your bread:</label>
            <select name="pao" id="pao" v-model="pao">
             <option value="">Select your bread</option>
             <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">
              {{ pao.tipo }}
            </option>
            </select>
            
           </div>
           <div class="input_container">
            <label for="Carne"> Choice the Meat to your burger :</label>
            <select name="carnes" id="carne" v-model="carne">
             <option value="">Select your Meat</option>
             <option  v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
            </select>
           </div>
           <div id="opcionais-container" class="input_container">
        <label id="opcionais-title" for="opcionais">Selecione os opcionais:</label>
        <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
          <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
          <span>{{ opcional.tipo }}</span>
        </div>
             
           </div>
           <div class="input_container">
             <input type="submit" class="submit-btn" value="Create my burger" >
           </div>
      </form>
     </div>
   </div>
</template>
<script>

import mensage from './mensagem.vue'
export default{
   name:'burgerForm',
   components:{
    mensage
    
},
   data(){
    return{
     paes: null,
     carnes :null,
     opcionaisdata :null,
     nome:null,
     pao:null,
     carne:null,
     opcionais:[],
     msg:null,
    }
   },
   methods:{
    async getIngredients(){
       const req = await fetch('http://localhost:3000/ingredientes')
       const data = await req.json()
       this.paes = data.paes
       this.carnes = data.carnes
       this.opcionaisdata = data.opcionais
    },
    async createBurger(e){
        e.preventDefault()
        
        const data = {
         nome:this.nome,
         carne: this.carne,
         pao: this.pao,
         opcionais:Array.from(this.opcionais),
         status:"solicitado",
        }

        const dataJson = JSON.stringify(data)

       const req = await fetch('http://localhost:3000/burgers',{
        method:"POST",
        headers:{"content-Type": "application/json"},
        body:dataJson
       })
       const res = await req.json()

       console.log('res', res);


        this.msg = `Pedido  Nº ${res.id} realizado com sucesso`
  
        setTimeout(()=> this.msg = '', 3000)
      
      this.nome = ''
      this.carne = ''
      this.pao = ''
      this.opcionais = ''
    }
 
   },

     mounted(){
     this.getIngredients()
     }
   
   }


</script>
<style scoped>
  #burger-form {
    max-width: 290px;
    margin: 0 auto;
    
  }

  .input_container {
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
  }

  label {
    font-weight: bold;
    margin-bottom: 15px;
    color: #222;;
    padding: 5px 10px;
    border-left: 4px solid #fcba03;
  }

  input, select {
    padding: 5px 10px;
    width: 300px;
  }

  #opcionais-container {
    flex-direction: row;
    flex-wrap: wrap;
  }

  #opcionais-title {
    width: 100%;
  }

  .checkbox-container {
    display: flex;
    align-items: flex-start;
    width: 50%;
    margin-bottom: 20px;
  }

  .checkbox-container span,
  .checkbox-container input {
    width: auto;
  }

  .checkbox-container span {
    margin-left: 6px;
    font-weight: bold;
  }

  .submit-btn {
    background-color: #222;
    color:#fcba03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
  }

  .submit-btn:hover {
    background-color: transparent;
    color: #222;
  }
</style>
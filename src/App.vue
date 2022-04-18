<template>
  <div id="app">
    <h2>Cadastro: </h2>
    <small id="Erro" v-show="deuErro"> O nome é invalido, tente novamente! </small><br>
    <input type="text" placeholder="name" v-model="nameField"><br>
    <input type="email" placeholder="email" v-model="emailField"><br>
    <input type="number" placeholder="phone number" v-model="numberField"><br>
    <button @click="cadastrarUsuario"> Cadastrar</button>
    <hr>  
    <div v-for="cliente in orderClientes" :key="cliente.id">
       <Clientes :cliente="cliente" :showNumber="true" @meDelete="deletarUsuario($event)"/>
    </div> 

  </div>
</template>

<script>
import _ from 'lodash';
import Clientes from './components/Clientes.vue';

export default {
  name: 'App',
  data(){
    return {
      deuErro: false,
      nameField: "", 
      emailField: "", 
      numberField: 0,
      clientes: [
        {
          id: 1,
          name: "Theo", 
          email: "theo@Dev.com", 
          number: 42367
        },
        {
          id: 2,
          name: "isabela", 
          email: "Isabela@Dev.com", 
          number: 2387248572893
        },
        {
          id: 3,
          name: "Arthur", 
          email: "Arthur@Dev.com", 
          number: 84093207
        },
      ]
    }
  },
  components: {
    Clientes
  },
  methods:{
    cadastrarUsuario: function(){
      if(this.nameField === " " || this.nameField.length < 3){
        this.deuErro = true;
      }else{
        this.clientes.push({name: this.nameField, email: this.emailField, number: this.numberField, id: Date.now()}),
        this.nameField = "";
        this.emailField = ""; 
        this.numberField = 0;
        this.deuErro = false;
      }
    },
    deletarUsuario: function($event){
      console.log("OLA")
      var id = $event.clienteId;
      var novoArray = this.clientes.filter(cliente => cliente.id != id);
      this.clientes = novoArray;
    }
  },
  computed: {
    orderClientes: function() {
      return _.orderBy(this.clientes, ['name'], ['asc']);
    }
  }
}
</script>

<style>
  #Erro{
    color: red;
  }
</style>

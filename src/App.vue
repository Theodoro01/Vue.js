<template>
  <div id="app">
    <h1>Guia Clientes </h1>
    <Clientes :cliente="clienteTheo" :showNumber="false"/> 

  </div>
</template>

<script>
 
import Clientes from './components/Clientes.vue'

export default {
  name: 'App',
  data(){
    return {
      clienteTheo: {
          name: "The cjb", 
          email: "theo@Dev.com", 
          number: 98765
      }
    }
  },
  components: {
    Clientes
  }
  
}
</script>

<style>

</style>

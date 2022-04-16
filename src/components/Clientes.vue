<template>
    <div :class="{'cliente': !isPremium, 'cliente-premium': isPremium }">
        
        <h2>Name:{{cliente.name}}</h2>
        <hr>
        <p> Email: {{cliente.email}}</p>
        <p v-if="showNumber === true">Phone number: {{cliente.number}}</p>
        <p v-else> Usuario não quer mostrar seu numero</p>
        <button @click="mudarCor"> Mudar cor!</button>
        <button @click="eventoDelete"> Deletar</button>
    </div>
</template>

<script> 
export default{
    data(){
        return{

            isPremium: false
            // name: "The cjb", 
            // email: "theo@Dev.com", 
            // number: 0,
        }
    },

    props: {
            cliente: Object, 
            showNumber: Boolean  
    },
    methods: {
        mudarCor: function(){
            this.isPremium = !this.isPremium; 
        },
        eventoDelete: function(){
            this.$emit("meDelete",{clienteId: this.cliente.id ,msg: "OLA", component: this});
        }
    }

    
}
</script>-
<style scoped>
    .cliente{
        color: red;
        background-color: navajowhite;
    }
    .cliente-premium{
        color: gold;
        background-color: black;
    }
</style>
<template>
    <div id="cliente">
        
        <h2>Name:{{cliente.name}}</h2>
        <hr>
        <p> Email: {{cliente.email}}</p>
        <p v-if="showNumber === true">Phone number: {{cliente.number}}</p>
        <p v-else> Usuario não quer mostrar seu numero</p>
    </div>
</template>

<script> 
export default{
    data(){
        return{
            // name: "The cjb", 
            // email: "theo@Dev.com", 
            // number: 0,
        }
    },

    props: {
            cliente: Object, 
            showNumber: Boolean  
    }
    
}
</script>

<style scoped>
    #cliente{
        color: red;
        background-color: navajowhite;
    }
</style>
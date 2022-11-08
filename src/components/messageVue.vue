<template lang="">
    <div>
        <div  v-show="show" class="message-container">
            <p @change="someMsg()">O pedido Nº {{numPedido}} foi {{msg}} com sucesso!</p>
        </div>
    </div>
</template>
<script>
export default {
    name: 'messageVue',
    props:{
        msg: String,
        numPedido: Number,
    },
    data(){
        return{
            show: false,
        }
    },
    methods:{
        someMsg(){
        this.show=true
            setTimeout(() => {
                this.show=false
            }, 3000);
        }
    },
 
   
}
</script>
<style scoped>
.message-container{
    color: #004085;
    background-color: #cce5ff;
    border: 2px solid #b8daff;
    border-radius: 5px;
    padding: 10px;
    max-width: 400px;
    margin: 30px auto;
}
    
</style>
<template lang="">
    <div id="burger-table" >
        <div>
          <messageVue ref="messageVue" :msg='msg' :numPedido='burgers_id'/> <!--COMPONENTE DE MSG -->
            <div id="burger-table-heading">
                <div class="order-id">Nº:</div>
                <div>Cliente:</div>
                <div>Pão:</div>
                <div>Carne:</div>
                <div>Queijo:</div>
                <div>Opcionais:</div>
                <div>Ações:</div>
            </div>
        </div>   
        <div id="burger-table-rows">
            <div class="burger-table-row" v-for="burger in burgers" :key="burger.id">
                <div class="order-number" >{{burger.id}}</div>
                <div>{{burger.nome}}</div>
                <div>{{burger.pao}}</div>
                <div>{{burger.carne}}</div>
                <div>{{burger.queijo}}</div>
                <div>
                    <ul>
                        <li v-for="(opcional, index) in burger.opcionais" :key="index">{{opcional}}</li>
                       
                    </ul>
                </div>
                <div id="btnID">
                    <select name="status" class="status" @change="updatedBurguer($event, burger.id),$refs.messageVue.someMsg()">
                        <option value="">selecione</option>
                        <option v-for="s in status" :key="s.id" :value="s.tipo" :selected="burger.status == s.tipo">{{s.tipo}}</option>
                    </select>
                    <button class="delete-btn" @click="deleteBurguer(burger.id), $refs.messageVue.someMsg()">Cancelar</button>
                </div>
            </div>

        </div>
    </div>            
</template>

<script>
import messageVue from './messageVue.vue'
export default {
    name: 'dashBoard',

    components:{
      messageVue
    },

    data(){
        return{
            burgers: null,
            burgers_id:null,
            status:[],
            msg:null,
        }
    },

    methods: {
        async getPedidos(){ //busca no banco os pedidos feitos para apresentar na dashboard
            const req = await fetch('http://localhost:3000/burgers')
            const data =await req.json()
            this.burgers=data


            //resgate status

            this.getStatus()

        },

        async getStatus(){ //pega a lista de status do banco e coloca no status[] da dashboard para poder escolher.
            const req = await fetch('http://localhost:3000/status')
            const data =await req.json()
            this.status=data
        },


        async deleteBurguer(id){
            const req =await fetch(`http://localhost:3000/burgers/${id}`,{
                method: 'DELETE'

            })
            //MENSAGEM DE EXCLUSAO DE PEDIDO
            this.msg='excluido'
            this.burgers_id=id

            this.getPedidos()
        },

        async updatedBurguer(eventObj,id){ //update do status do hamburguer. Para manter atualizado mesmo quando reload na pag.

            const option = eventObj.target.value //pegando o valor colocado no select do status

            const dataJson = JSON.stringify({status: option})

            const req =await fetch(`http://localhost:3000/burgers/${id}`,{
                method: 'PATCH',
                headers: {'Content-Type': 'application/json'},
                body: dataJson,
            })

              //MENSAGEM DE ALTERACAO:
            this.msg=`alterado para ${option}`
            this.burgers_id=id
        }

    },

    mounted(){
        this.getPedidos()
    }
}
</script>


<style scoped>

  #burger-table {
    max-width: 1200px;
    margin: 0 auto;
    min-height: 400px;
  }
  #burger-table-heading,
  #burger-table-rows,
  .burger-table-row {
    display: flex;
    flex-wrap: wrap;
  }
  #burger-table-heading {
    font-weight: bold;
    padding: 12px;
    border-bottom: 3px solid #333;
    font-size: 1.6rem;

  }
  .burger-table-row {
    width: 100%;
    padding: 12px;
    border-bottom: 1px solid rgb(102, 101, 101);
    font-size: 1.6rem;
  }
  #burger-table-heading div,
  .burger-table-row div {
    width: 15%;
  }
  #burger-table-heading .order-id,
  .burger-table-row .order-number {
    width: 6%;
  }
  select {
    padding: 12px 6px;
    margin-right: 12px;
    height: 40px;
  }
  .delete-btn {
    background-color: #222;
    color:#fcba03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 1.6rem;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
    max-height: 38px;
  }

  #btnID{
    display: flex;
    align-items: center;
  }

  .delete-btn:hover {
    background-color: transparent;
    color: #222;
  }

  .status option{
    max-height: fit-content;
  }
   
</style>
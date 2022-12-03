<template lang="">

    <div>
        <!-- COMPONENTE MSG -->
        <messageVue  ref="messageVue" :msg="msg"  :numPedido="numPedido" v-show='true'/>
    </div>
    <form id="burger-form" @submit.prevent="createBurguer(),$refs.messageVue.someMsg()">
        <div class="input-container">
            <label class="nomeCliente"  for="nome">Seu nome:</label>
            <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome">
        </div>
        <div class="input-container">
            <label for="pao">Escolha o pão:</label>
            <select name="pao" id="pao" v-model="pao">
            <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">{{pao.tipo}}</option>
            </select>
        </div>
        <div class="input-container">
            <label for="carne">Escolha a carne:</label>
            <select name="carne" id="carne" v-model="carne">
            <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{carne.tipo}}</option>
            </select>
        </div>
        <div class="input-container">
            <label for="queijo">Escolha o queijo:</label>
            <select name="queijo" id="queijo" v-model="queijo">
            <option v-for="queijo in queijos" :key="queijo.id" :value="queijo.tipo">{{queijo.tipo}}</option>
            </select>
        </div>

        <div id="opcionais-container" class="input-container" >
            <label id="opcionais-title" for="opcionais">Selecione os opcionais:</label>
            <div class="checkbox-container" v-for="opcional in opcionaisdata" :key="opcional.id">
                <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo">
                <span >{{opcional.tipo}}</span>
            </div>

        </div>
        <div class="input-container">
            <input type="submit" class="submit-btn" value="Criar meu hamburguer">
        </div>
       
    </form>

</template>


<script>
import messageVue from './messageVue.vue'

export default {
    name: 'burguerForm',
    components:{
        messageVue
    },
    data(){
        return{
            paes:null,
            carnes:null,
            queijos:null,
            opcionaisdata:null,

            nome:null,
            pao:null,
            carne:null,
            queijo:null,
            status:'Solicitado',
            msg:null,
            opcionais:[],

            numPedido:null,
        }
    },
    methods: {

        //1-Pegar ingredientes do banco de dados para preencher no form de montagem do burger:
       async getIngredientes(){
            const req = await fetch('http://localhost:3000/ingredientes')
            const data = await req.json()
            
            this.paes= data.paes
            this.carnes=data.carnes
            this.opcionaisdata= data.opcionais
            this.queijos=data.queijos
        },

        //2-Mandar o burger montado para o banco de dados:
        async createBurguer(){
            const data={ //dados do hamburger que irao para o banco
                nome: this.nome,
                carne:this.carne,
                pao: this.pao,
                queijo:this.queijo,
                opcionais:Array.from(this.opcionais),
                status:'Solicitado'
            }
            const dataJson= JSON.stringify(data); //trocar o json para string para poder enviar para o banco
            const req = await fetch('http://localhost:3000/burgers',{ //POST para colocar os dados no banco
                method:'POST',
                headers:{'content-type':'application/json'},
                body: dataJson
            })
            
            const res = await req.json()
            console.log(res)
            
//MSG PEDIDO REALIZADO
            this.msg = 'realizado'
            this.numPedido = res.id

        

            //limpando os dados do burger form
            this.nome=''
            this.carne=''
            this.pao=''
            this.opcionais=[]
            this.queijo=''
        }

    },
    mounted() { //ao montar o componente, puxar os dados do banco.
        this.getIngredientes()
    },
    
}
</script>


<style scoped>

#burger-form{
    max-width: 400px;
    height: fit-content;
    margin: 0 auto;
    padding-left: 30px;
    background-color: rgb(240, 239, 239);
    border: 2px solid #221;
    border-radius: 20px;
    font-size: 1.8rem;
}

.input-container{
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
}

label{
    font-weight: bold;
    margin-bottom: 15px;
    color: #222;
    padding: 5px 10px;
    margin-left: 4px solid #fcba03;
}

.nomeCliente{
    margin-top: 20px;
}

input, select{
padding: 5px 10px;
width: 300px;
}

#opcionais-container{
    flex-direction: row;
    flex-wrap: wrap;
}

#opcionais-title{
    width: 100%;
}

.checkbox-container{
    display: flex;
    align-items: flex-start;
    width: 50%;
    margin-bottom: 20px;
}

.checkbox-container span, .checkbox-container input{
    width: auto;
}
.checkbox-container span{
    margin-left: 6px;
    font-weight: bold;
}

.submit-btn{
    background-color: #222;
    color:#fcba03;
    font-weight: bold;
    border:2px solid #222;
    padding: 1rem;
    font-size: 1.6rem;
    margin-left: 1rem;
    margin-bottom: 2rem;
    cursor: pointer;
    transition: .5s;
}
.submit-btn:hover{
    background-color: transparent;
    color:#222;
}

@media (max-width: 352px){
    .submit-btn{
        max-width :25rem;;
    }
}

/* ponto de quebra é width300px  */


    
</style>
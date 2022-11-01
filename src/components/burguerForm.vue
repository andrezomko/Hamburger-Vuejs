<template lang="">

    <div>
        <p>componnente msg</p>
    </div>
    <form id="burguer-form">
        <div class="input-container">
            <label class="nomeCliente"  for="nome">Nome do cliente:</label>
            <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite o seu nome">
        </div>
        <div class="input-container">
            <label for="pao">Escolha o pão:</label>
            <select name="pao" id="pao" v-model="pao">
            <option value="">pão</option>
            <option value="integral">integral</option>
            <option value="3 queijos">3 queijos</option>
            <option value="brioche">brioche</option>
            <option value="ervas finas">ervas finas</option>
            </select>
        </div>
        <div class="input-container">
            <label for="carne">Escolha a carne:</label>
            <select name="carne" id="carne" v-model="carne">
            <option value="">selecione sua carne:</option>
            <option value="maminha">maminha</option>
            <option value="alcatra">alcatra</option>
            <option value="picanha">picanha</option>
            </select>
        </div>
        <div class="input-container">
            <label for="queijo">Escolha o queijo:</label>
            <select name="queijo" id="queijo" v-model="carne">
            <option value="">selecione o queijo:</option>
            <option value="prato">prato</option>
            <option value="cheddar">cheddar</option>
            <option value="provolone">provolone</option>
            <option value="gorgonzola">gorgonzola</option>
            </select>
        </div>
        <div id="opcionais-container" class="input-container" >
            <label id="opcionais-title" for="opcionais">Selecione os opcionais:</label>
            <div class="checkbox-container">
                <input type="checkbox" name="opcionais" v-model="opcionais" value="cebola">
                <span>Cebola</span>
            </div>
            <div class="checkbox-container">
                <input type="checkbox" name="opcionais" v-model="opcionais" value="bacon">
                <span>Bacon</span>
            </div>
            <div class="checkbox-container">
                <input type="checkbox" name="opcionais" v-model="opcionais" value="salada">
                <span>Salada</span>
            </div>
            <div class="checkbox-container">
                <input type="checkbox" name="opcionais" v-model="opcionais" value="picles">
                <span>Picles</span>
            </div>
        </div>
        <div class="input-container">
            <input type="submit" class="submit-btn" value="Criar meu hamburguer">
        </div>
       
    </form>

</template>


<script>
export default {
    name: 'burguerForm'
    
}
</script>


<style scoped>



#burguer-form{
    max-width: 400px;
    height: fit-content;
    margin: 0 auto;
    padding-left: 30px;
    background-color: rgb(240, 239, 239);
    border: 2px solid #221;
    border-radius: 20px;
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
    padding: 10px;
    font-size: 16px;
    margin-left: 10px;
    margin-bottom: 20px;
    cursor: pointer;
    transition: .5s;
}
.submit-btn:hover{
    background-color: transparent;
    color:#222;

}
    
</style>
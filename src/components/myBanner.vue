<template lang="">
    <div id="main-banner">
        <h1 id="dropDown" @click="dropDownMethod" >Make Your Burger</h1>
    </div>
</template>
<script>
export default {
    name:'myBanner', 
    methods:{
        dropDownMethod(){
            window.scrollTo(0,600)
        }
    }
}
</script>
<style scoped>


#main-banner{
    background-image: url('../../public/img/junioReis.jpg');
    background-position: center;
    background-size: cover;
    height: 50rem;
    display: flex;
    align-items: center;
    justify-content:flex-start;
    min-width: 34rem;
    max-width: 100vw;;

}

h1{
    color: rgb(210, 205, 205);
    text-align: left;
    font-size: 6rem;
    background-color: #222;
    padding: 2rem;
    margin-left: 0;
    transition: .6s;  
   
}

h1:hover{
    color: #fcba03;
    cursor: pointer;
}

@media (max-width: 664px){

    h1{
        min-width: 30rem;
        font-size: clamp(2rem, 3rem, 5rem);
        justify-self: flex-start;   
    }
}
</style>
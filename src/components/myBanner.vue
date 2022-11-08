<template lang="">
    <div id="main-banner">
        <h1>Make Your Burguer</h1>
    </div>
</template>
<script>
export default {
    name:'myBanner',

    
}
</script>
<style scoped>


#main-banner{
    background-image: url('../../public/img/burger.jpeg');
    background-position: center;
    background-size: cover;
    height: 50rem;
    display: flex;
    align-items: center;
    justify-content:flex-start;
    min-width: 34rem;
    max-width: 100vw;;


}

/* agora preciso:
- responsiv navbar
- responsiv burger form */

h1{
    color: white;
    text-align: left;
    font-size: 6rem;
    background-color: #222;
    padding: 2rem;
    margin-left: 0;
}

@media (max-width: 664px){

    h1{
        min-width: 30rem;
        font-size: clamp(2rem, 3rem, 5rem);
        justify-self: flex-start;
        
    }
}




/* Responsividade */

/* mobile S */
/* @media (max-width:340px){
    #main-banner{
        width: 340px;
        background-size: cover;
        background-position: center;
    }  
    #main-banner h1{
        font-size: 20px;
    }
} */

/* mobile M */
 /* @media (min-width: 341px)  {

    #main-banner{
        background-size: cover;
        background-position: center;
    }
    #main-banner h1{
        font-size: 1.6rem;
    }

 } */

/* mobile G  */

/* @media (min-width: 425px) and (max-width: 600px){

    #main-banner{
        background-size: cover;
        background-position: center;
    }
    #main-banner h1{
        font-size: 36px;
    }
} */


 
</style>
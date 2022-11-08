<template>
<myBanner/>
  <div class="main-container">
   <h1>Monte o seu hamburguer!</h1>
   <burguerForm/>
  </div>
</template>

<style>
:root{
  font-size: 62.5%;
}



.main-container{
  background-color: rgb(218, 215, 215);
  margin:0;
  padding-top: 4rem;
  padding-bottom: 4rem;
}

@media (max-width: 340px) {

  .main-container{
    min-width: 340px;
  }
  
  h1{

    margin: 10px auto;
    font-size:2rem;
  }
}


</style>


<script>
import myBanner from '@/components/myBanner.vue';
import burguerForm from '../components/burguerForm.vue'

export default{
  name: 'HomeView',
  components:{
    myBanner,
    burguerForm
  }
}
</script>

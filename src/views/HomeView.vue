<template>
<myBanner/>
  <div  class="main-container">
   <h1>Monte o seu hamburguer!</h1>
   <burguerForm/>
  </div>
</template>

<style>
.main-container{
background-color: rgb(218, 215, 215);
 margin: 0; 
 padding-top: 40px;
 padding-bottom: 40px;
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

<template>
  <navBar :logotipo="logo_src" :alt="app_name" />
  <router-view/>
  <theFooter/>
</template>

<script>
import navBar from './components/navBar.vue';
import theFooter from './components/theFooter.vue';

export default {
  components: {
    navBar,
    theFooter,
  },
  data(){
    return{
      logo_src: '/img/logo.png' ,
      app_name: 'Make Your Burguer'
    }
  }
}

</script>

<style>

*{
    font-family: Arial, Helvetica, sans-serif;
    padding:0;
    margin: 0;
    box-sizing: border-box;
}

.main-container{
margin: 100px;
height: 100%;
  /* min-height: 42vh;
   */
   /* min-height: 345px; */

}

h1{
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}

</style>

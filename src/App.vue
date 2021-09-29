<template>
  <div>
    <Navbar/>
    <div>
      <router-view></router-view>
    </div>
    <Footer/>
  </div>
  
</template>

<script>

import Navbar from "../src/components/Navbar.vue"
import Footer from "../src/components/Footer.vue"


export default {
  setup(){
      return{

      }
  },

  components:{
   
    Navbar,
    Footer
  } 

}
</script>

<style>
  * {
    font-family: Helvetica;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }
  
  h1 {
    text-align: center;
    font-size: 42px;
    margin-bottom: 30px;
    color: #222;
  }
</style>
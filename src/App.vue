<template>
  <div id="app">
  
    <poke-guia></poke-guia>
  </div>
</template>

<script>
import pokeguiaComponent from "./components/pokeguiaComponent.vue"
  export default {
    data() {
      return {
      };
    },
    components:{
      'poke-guia': pokeguiaComponent,
    }
  }
</script>
<style>
body{
background-image:url("/src/img/Mosaico.png");
background-size:cover;
background-repeat:repeat;
width:100%;
}
</style>

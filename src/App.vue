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

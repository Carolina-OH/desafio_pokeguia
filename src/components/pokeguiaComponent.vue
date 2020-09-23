<template>
<div>
    <nav class="navbar navbar-light bg-danger">
  <a class="navbar-brand" href="#">
    <img src="src/img/pokemon-23.svg" width="200" height="100" alt="" loading="lazy">
  </a>
   <a class="navbar-brand" href="#">
    <img src="src/img/pokeball.svg" width="80" height="80" alt="" loading="lazy">
  </a>
</nav>
<div class="d-flex justify-content-center">
  <div class="card text-center mt-5">
    <h1>{{tittle}}</h1>
    <label>Nombre</label>
    <input id="personaje" type="text" class="form-control text-center" v-model="personaje.nombre"><br>
    <button type="button" class="btn btn-danger" @click.prevent="fetchPersonaje">Buscar</button>
    <img class="mt-5" :src="" alt="">
    <p>Movimientos</p>
    <ul>
      <li></li>
    </ul>
    <p>Habilidades</p>
    <ul>
      <li></li>
    </ul>
  </div>
  </div>
</div>
</template>

<script>
export default {
    name: 'pokeguia',
    // props: {},
    data: function(){
        return {
            tittle: "Pokeguía",
            personaje:{
            nombre:"",
            movimientos:"",
            habilidades:"",
            imagen:"",
            },
        }
    },
    // computed: {
    //   image(){
    //     return
    //     //this.personaje.sprites.front_default
    //   }
    },
    methods: {
        fetchPersonaje(){

          fetch(`https://pokeapi.co/api/v2/pokemon/${this.personaje.nombre}/`)
          .then (response=> response.json())
          .then(json=>{
            console.log(json)
            //this.addPersonaje(json);
          })
          .catch(error=>{
            console.log(error)
          })
        }
    },
   // addPersonaje(json){
     // if (json.results === undefined){
     // alert("personaje no encontrado")
      //return;      
      //}
      //this.personaje=json.results;
    }
    // components: {},
}
</script>

<style scoped>
  input{
    width:200px;
    margin:0 20% 0 20%;
  }
  button{
    width:200px;
  }


  .card{
    width:350px;
    display:flex;
    justify-content:center;
    margin:0 20% 0 20%;
    }
</style>
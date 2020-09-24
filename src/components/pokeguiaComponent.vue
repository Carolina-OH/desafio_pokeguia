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
    <img class="mt-5" :src="image.front_default" alt="">
    <p>Movimientos</p>
    <ul>
      <li v-for="(movimiento,index) in movimientos" :key="index">{{movimiento.move.name}}</li>
    </ul>
    <p>Habilidades</p>
    <ul>
       <li v-for="(habilidad,index) in habilidades" :key="index">{{habilidad.ability.name}}</li>
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
            movimiento:"",
            movimientos:[],
            habilidades:[],
            habilidad:"",
            sprites:[],
            },
        }
    },
     computed: {
       image(){
         return this.personaje.sprites;
       },
      habilidades(){
       return this.personaje.abilities;
      },
      movimientos(){
        return this.personaje.moves;
      }
     },
    methods: {
        fetchPersonaje(){
          fetch(`https://pokeapi.co/api/v2/pokemon/${this.personaje.nombre}`)
          .then (response=> response.json())
          .then(json=>{
            console.log(json)
            this.personaje=json;
          })
          .catch(error=>{
            alert("personaje no encontrado")
            console.log(error)
          })
        }
    ,
    addPersonaje(json){
      console.log(json)
      // if (JSON.parse){
      // alert("personaje no encontrado")
       return;      
      // }
      this.personaje=json.results;
    }
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
    margin:20px 20% 20px 20%;
  }


  .card{
    width:350px;
    display:flex;
    justify-content:center;
    margin:0 20% 0 20%;
    }

    ul{
      color:black;
    }
</style>
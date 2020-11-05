<template>
<div>
    <nav class="navbar navbar-light bg-danger">
  <a class="navbar-brand" href="#">
    <img src="https://raw.githubusercontent.com/Carolina-OH/pokeguia.github.io/c16376fabc9dcedfdffbdf35e8db9fa420ca4b36/Pokemon-23.svg" width="300" height="100" alt="" loading="lazy">
  </a>
   <a class="navbar-brand" href="#">
    <img src="https://raw.githubusercontent.com/Carolina-OH/pokeguia.github.io/c16376fabc9dcedfdffbdf35e8db9fa420ca4b36/Pokeball.svg" width="80" height="80" alt="" loading="lazy">
  </a>
</nav>
<div class="cuerpo d-flex justify-content-center">
  <div class="card text-center mt-5">
    <h1 class="titulo-poke mt-4">{{tittle}}</h1>
    <label>Nombre</label>
    <input id="personaje" type="text" class="form-control text-center" v-model="personaje.nombre"><br>
    <button type="button" class="btn btn-danger" @click.prevent="fetchPersonaje">Buscar</button>
    <img class="mt-2" id="poke" :src="image.front_default" alt="">
    <h3 class="font-weight-bold">Movimientos</h3>
    <ul>
      <li v-for="(movimiento,index) in movimientos" :key="index">{{movimiento.move.name}}</li>
    </ul>
    <h3 class="font-weight-bold">Habilidades</h3>
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
            tittle: "PokeGuía",
            personaje:{
            nombre:"",
            movimiento:"",
            movimientos:[],
            habilidades:[],
            habilidad:"",
            sprites:{
              front_default:"",
            },
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
   },
   created:function(){
     this.fetchPersonaje;
   },
   mounted:function(){
     this.personaje.nombre="pikachu"
     this.fetchPersonaje();
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
  #poke{
    width:100px;
    align-self:center;
  }

  .card{
    width:350px;
    display:flex;
    justify-content:center;
    margin:0 20% 20px 20%;
    border:1px solid black;
    background-color:lightblue;
    }
    
    ul li{
      list-style:none;
      margin-right:30px;
    }
    .titulo-poke,h3{
      font-family: 'Balsamiq Sans', cursive;
      color:rgb(255,203,5);
      text-shadow:-4px 0 rgb(23,67,124), -2px 1px rgb(23,67,124), 1px 0 rgb(23,67,124), 0 -1px rgb(23,67,124);
      border-color:rgb(23,67,124);
    }


</style>
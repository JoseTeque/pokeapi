<template>
  <div id="pekeapi">
      <h1>PokeGuía</h1>
      <div>
        <input v-model="pokemonName" type="text" placeholder="Ingrese el pokemon">
        <button @click="searchpokemon">Buscar</button>
      </div>
      <div class="imagen-nombre">
          <img v-if="currentPokemon.sprites" :src="currentPokemon.sprites.front_default" alt="">
           <p>{{currentPokemon.name}}</p>
      </div>
     <h3>MOVES</h3>
   <ul>
       <li v-for="move in currentPokemon.moves" :key="move.name">
           {{move.move.name}}
       </li>
       <li></li>
   </ul>
   <h3>ABILITIES</h3>
   <ul>
       <li v-for="ability in currentPokemon.abilities" :key="ability.name">
           {{ability.ability.name}}
       </li>
   </ul>
  </div>
</template>

<script>
export default {
    data(){
        return{
            currentPokemon:{},
            pokemonName: ""
        }
    },
    async created(){
         const Baseurl = "https://pokeapi.co/api/v2/pokemon";

            const response =  await fetch(`${Baseurl}/pikachu`)

            const respuesta = await response.json();

            this.currentPokemon = respuesta;
    },
    methods: {
        async searchpokemon(){
            const Baseurl = "https://pokeapi.co/api/v2/pokemon";

            const response =  await fetch(`${Baseurl}/${this.lower}`)

            const respuesta = await response.json();

            this.currentPokemon = respuesta;

            this.pokemonName = "";
        }
    },
    computed:{
        moves(){
            return this.currentPokemon.moves
        },
        abilities(){
            return this.currentPokemon.abilities
        },
        lower(){
            return this.pokemonName.toLowerCase()
        }
    }
}
</script>

<style>
#pekeapi {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

ul{
    list-style: none;
}

#pokeapi img{
    text-align: center;
}

.imagen-nombre{
    display: flex;
    justify-content: center;
    align-items: center;
}

.imagen-nombre p{
    font-weight: 700;
    font-size: 16px;
}
</style>

<template>
    <div>
      <div v-for="(poke, index) in pokemons" :key="index">
        <PokemonComponent :name="poke.name" :url="poke.url" :num="index+1" />
      </div>
    </div>
</template>

<script>
import axios from 'axios'
import PokemonComponent from './components/Pokemon';

export default {
  name: 'App',
  data(){
    return {
      pokemons: []
    }
  },
  created: function(){
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0").then(res => {
      console.log("Lista recebida");
      this.pokemons = res.data.results;
    })
  },
  components: {
    PokemonComponent
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

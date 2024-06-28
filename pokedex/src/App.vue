<template>
  <div id="app">
    <div class="column is-half is-offset-one-quarter" >
      <!-- <div v-for="(poke, index) in pokemons" :key="index">
        <pokemon :name="poke.name" :url="poke.url" :num="index + 1"/>
      </div> -->

      <input class="input is-rounded" type="text" name="" id="" placeholder="Buscar pokemon pelo nome..." v-model="busca">
      <br><button class="button is-fullwidth is-success" id="buscaBtn">Buscar </button>
      <div>
        <pokemon :name="Charizard" :url="AAA" :num="  1"/>
      </div>
    </div>  
  </div>
</template>

<script>
import axios from "axios";
import pokemon from './components/pokemon';

export default {
  name: "App",
  data() {
    return {
      busca: '',
      pokemons: [],
    };
  },
  create: function () {
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0")
      .then((res) => {
        this.pokemons = res.data.results;
      });
  },
  components:{
    pokemon
  },
  computed: {
    resultadoBusca: function(){
      if(this.busca =='' || this.busca == ' '){
          return this.pokemons
        }else{
          return this.pokemons.filter(pokemon => pokemon.name)  
        }

      }
    }
  
};
</script>

<style>

</style>

<template>
 <v-app>
   <v-container>
    <v-card>
      <v-row>
        <v-col cols="2" 
        v-for="pokemon in pokemons" 
        :key="pokemon.name">
        <v-card>
          <v-container>
            <v-row class="mx-0 d-flex justify-center">
              <img :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${get_id (pokemon)}.png`" :alt="pokemon.name" width="70%">
            </v-row>
            <h3 class="text-center capitalize"> {{get_name (pokemon)}}</h3>
          </v-container>
        </v-card>

        </v-col>
      </v-row>
    </v-card>
  </v-container>

 </v-app>
</template>

<script>

import axios from 'axios';

export default {
  name: 'App',

  components: {
 
  },

data (){
  return {
    pokemons: []
  }
},
methods: {
  get_id (pokemon) {
    let url = pokemon.url;
    let id = url.split('/')[url.split('/').length - 2];
    return id;
  },
  get_name (pokemon) {
    return pokemon.name.charAt(0).toUpperCase(0) + pokemon.name.slice(1)
  }

},

  mounted (){
    axios.get('https://pokeapi.co/api/v2/pokemon?limit=151')
    .then(response => {
      this.pokemons = response.data.results;
    })
    .catch(error => {
      console.log(error);
    })
  }
};

</script>

<style>
#app {
  background: rgb(2,0,36);
  background: linear-gradient(90deg, rgba(2,0,36,0.9023984593837535) 0%, rgba(9,121,93,1) 80%, rgba(73,88,91,1) 100%);
}
</style>
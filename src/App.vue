<template>
 <v-app>
   <v-container>
    <v-card>
      <v-row>
        <v-col cols="2" 
        v-for="pokemon in pokemons.slice(0,10)" 
        :key="pokemon.name">
        <v-card>
          <v-container>
            <h2 class="text-center"> {{pokemon.name}} </h2>
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
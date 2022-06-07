<template>
  <v-card 
    class="mx-auto my-12"
    max-width="374">

    <template slot="progress">
      <v-progress-linear
        color="purple-deep" height="10"
        indeterminate></v-progress-linear>
    </template>

    <div v-if="pokemonInfo">
      <v-img
        :src="pokemonInfo.sprites.front_default"></v-img>
      
      <v-card-title>
        {{ pokemonInfo.name }}
      </v-card-title>
      
      <v-card-text>
        <v-card-title>
          Tipo:
        </v-card-title>
        <div>
          {{ pokemonInfo.species.name }}
        </div>
      </v-card-text>
    </div>
  
  </v-card>
</template>

<script>
import pokemonApi from "@/api/pokemonApi";
  export default {
    props: {
      dataPokemon: Object
      },
      mounted() {
        this.getIfoPokemon()
      },
    data() {
      return { 
        loading: false,
        pokemonInfo: null, 
      }
    },
    methods: {
      getIfoPokemon(){
        pokemonApi.get(`/${ this.dataPokemon.name }`).then(response => this.pokemonInfo = response.data);
      },
      PokeEvolution () {
        this.loading = true
        setTimeout( ()=> ( this.loading = false ), 2000 )
      }
    },

  }
</script>

<style>

</style>
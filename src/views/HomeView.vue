<template>
  <v-list>
    <v-list-item v-for="( item, index ) in pokemons.results" :key="index">
      <PokeCard :dataPokemon="item"></PokeCard>
    </v-list-item>
  </v-list>
</template>

<script>
// @ is an alias to /src
import PokeCard from '@/components/PokeCard.vue'
// import pokemonApi from '@/api/pokemonApi';

export default {
  name: 'HomeView',
  components: {
    PokeCard,
  },
  data() {
    return {
      pokemons: {
        results: []
      }
    }
  },
  mounted() {

    this.getPokemons()

  },
  methods: {
    getPokemons() {
      this.$pokemonApi.get('/').then( reponse => this.pokemons = reponse.data)
    }
  }
}
</script>

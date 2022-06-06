<template>
  <PokeCard :name="pollo" :pokeImg="pokeImg" :ability="ability"></PokeCard>
</template>

<script>
// @ is an alias to /src
import PokeCard from '@/components/PokeCard.vue'

export default {
  name: 'HomeView',
  components: {
    PokeCard,
  },
  data() {
    return {
      pollo: 'pablito',
      pokeImg: 'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/132.svg',
      ability: 'salchichas con queso'
    }
  },
}
</script>

<template>
  <PokeCard></PokeCard>
</template>

<script>
// @ is an alias to /src
import PokeCard from '@/components/PokeCard.vue'

export default {
  name: 'HomeView',
  components: {
    PokeCard,
}
}
</script>

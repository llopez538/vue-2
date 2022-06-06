<template>
  <v-card 
    class="mx-auto my-12"
    max-width="374">

    <template slot="progress">
      <v-progress-linear
        color="purple-deep" height="10"
        indeterminate></v-progress-linear>
    </template>

    <v-img
      height="250"
      :src="pokeImg"></v-img>
    
    <v-card-title>{{ name }}</v-card-title>
    
    <v-card-text>
      <div>
        {{ ability }}
      </div>
    </v-card-text>
  
  </v-card>
</template>

<script>
  export default {
    props: [
      'name',
      'pokeImg',
      'ability'
      ],
    data: () =>({
      loading: false,
    }),
    methods: {
      PokeEvolution () {
        this.loading = true

        setTimeout( ()=> ( this.loading = false ), 2000 )
      }
    },

  }
</script>

<style>

</style>
<template>
  <v-app>
    <v-app-bar app>
      <router-link to="/" custom v-slot="{ navigate }">
        <span @click="navigate" keypress.enter="navigate" role="link">
        {{ appTitle }}
        </span>
      </router-link>

      <v-spacer></v-spacer>

      <v-btn text v-for="item in menuItems" :key="item.tile" :to="item.path">
        <v-icon left dark small>{{ item.icon }}</v-icon>
        {{ item.title }}
      </v-btn> 
    </v-app-bar>

    <!-- Sizes your content based upon application components -->
    <v-main>
      <v-container fluid>

          <router-view v-slot="{ Component, route }">
            <component :is="Component" :key="route.name"></component>
          </router-view>
      </v-container>
    </v-main>

  </v-app>
</template>

<script>
import Vue from "vue";
import axios from "axios";

const pokemonApi = axios.create({
    baseURL: 'https://pokeapi.co/api/v2/pokemon'
})

Vue.prototype.$pokemonApi = pokemonApi

export default {
  name: 'App',
  data() {

    return {
      appTitle: 'Learning VueJs',
      sidebar: false,
      menuItems: [
        { title: 'Home', path: '/home', icon: 'mdi-arrow-left' },
        { title: 'About', path: '/about', icon: 'mdi-checkbox-marked-circle' },
        { title: 'Contact', path: '/contact', icon: 'mdi-account-circle' },
      ]
    }

  }
}
</script>

<style lang="scss">
/*
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
*/
</style>

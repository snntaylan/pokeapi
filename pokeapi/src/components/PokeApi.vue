<template>
  <div class="pokeapi">
    <ul>
      <input v-on:input="getPokemon()" v-model="query" placeholder="Pokemon name">
      <br>
      <p>Search: {{query}}</p>
      <PokeAbilities v-if="pokemon" v-bind:pokemon="pokemon"/>
      <h4 v-else>Pokemon could not found !</h4>
    </ul>
  </div>
</template>

<script>
import PokeAbilities from "./PokeAbilities.vue";
import axios from "axios";
import {
  cacheAdapterEnhancer,
  throttleAdapterEnhancer
} from "axios-extensions";
const http = axios.create({
  baseURL: "/",
  headers: { "Cache-Control": "no-cache" },
  adapter: throttleAdapterEnhancer(cacheAdapterEnhancer(axios.defaults.adapter))
});

export default {
  name: "PokeApi",
  components: {
    PokeAbilities
  },
  data() {
    return {
      query: "",
      pokemon: null
    };
  },
  methods: {
    getPokemon: function() {
      if (this.query === "") this.pokemon = null;
      else {
        http
          .get("https://pokeapi.co/api/v2/pokemon/" + this.query)
          .then(response => {
            this.pokemon = response.data;
          })
          .catch(error => {
            this.pokemon = null;
            if (error.response && error.response.status === 404)
              console.log("Pokemon does not exist !");
          });
      }
    }
  }
};
</script>

<style scoped>
img {
  width: 100px;
}
input {
  width: 200px;
}
.pokeapi {
  background-color: transparent !important;
  display: flex;
  flex-direction: row;
  justify-content: center;
}
</style>

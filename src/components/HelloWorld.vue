<template>
  <v-container fluid>
    <h1 class="text-center">List of Pokemons</h1>
    <v-row>
      <v-col cols="12" sm="6" md="4" v-for="(pokemon, index) in pokemonList" :key="index">
        <PokemonCard :urlPokemon="pokemon.url" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from "axios";
import PokemonCard from "./PokemonCard";

export default {
  name: "HelloWorld",
  components: {
    PokemonCard
  },
  data() {
    return {
      pokemonList: []
    };
  },
  created() {
    const externalService = "https://pokeapi.co/api/v2";
    const resource = `${externalService}/pokemon`;
    // Load
    this.loadPokemons(resource);
  },
  methods: {
    loadPokemons(resource) {
      console.log("Loading pokemons...");

      console.log(`Querying to resource: ${resource}`);

      // Connect to API: https://pokeapi.co/api/v2
      axios
        .get(resource)
        .then(response => {
          console.log("\nresponse-->", response);
          const { data } = response;

          if (data !== null && data !== undefined) {
            const { results } = data;
            if (results !== null && results !== undefined) {
              console.log("results", results);
              this.pokemonList = results;
            }
          }
        })
        .catch(error => {
          console.error(error);
        });
    }
  }
};
</script>

<style lang="scss" scoped>
</style>
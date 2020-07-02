<template>
  <v-card>
    <v-toolbar color="primary" dark class="justify-center">{{pokemon.name | uppercase}}</v-toolbar>
    <v-card-text>{{urlPokemon}}</v-card-text>
    <v-card-actions>
      <v-btn small block color="secondary">See more</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
import axios from "axios";

export default {
  props: ["urlPokemon"],
  name: "PokemonCard",
  data() {
    return {
      pokemon: {}
    };
  },
  filters: {
    uppercase: function(value) {
      if (!value) return "";
      value = value.toString();
      return value.toUpperCase();
    }
  },
  created() {
    this.loadPokemon(this.urlPokemon);
  },
  methods: {
    loadPokemon(resource) {
      console.log("urlPokemon", this.urlPokemon);
      console.log(`Querying to resource: ${resource}`);

      // Connect to API: https://pokeapi.co/api/v2
      axios
        .get(resource)
        .then(response => {
          console.log("\nresponse-->", response);
          const { data } = response;
          console.log(data);
          this.pokemon = data;

          // if (data !== null && data !== undefined) {
          //   const { results } = data;
          //   if (results !== null && results !== undefined) {
          //     console.log("results", results);
          //     this.pokemonList = results;
          //   }
          // }
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
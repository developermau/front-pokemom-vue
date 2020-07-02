<template>
  <v-card>
    <v-toolbar color="primary" dark class="justify-center">{{pokemon.name | uppercase}}</v-toolbar>
    <v-card-text>
      <v-img
        v-if="pokemon.sprites !== undefined"
        :src="pokemon.sprites.front_default"
        aspect-ratio="2"
        contain
      ></v-img>
    </v-card-text>
    <v-card-actions>
      <v-btn small block color="secondary" :to="`pokemon/${getPokemonIdFromURL(urlPokemon)}`">See more</v-btn>
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
          const { data } = response;
          // console.log(data);

          if (data !== null && data !== undefined) {
            this.pokemon = data;
            const { sprites } = this.pokemon;

            if (sprites !== null && sprites !== undefined) {
              console.log("sprites", sprites);
              this.pokemonList = sprites;
            }
          }
        })
        .catch(error => {
          console.error(error);
        });
    },
    getPokemonIdFromURL(url){
      // Example: https://pokeapi.co/api/v2/pokemon/9/
      console.log("url", url);

      url = url.replace("https://pokeapi.co/api/v2/pokemon/", "");

      return url;
    }
  }
};
</script>

<style lang="scss" scoped>
</style>
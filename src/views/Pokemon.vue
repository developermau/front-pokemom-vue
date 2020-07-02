<template>
  <v-container fluid class="justify-center">
    <h1 class="text-center">{{pokemon.name | uppercase}}</h1>
    <v-card elevation="2" outlined>
      <v-card-text>
        <v-row class="text-center">
          <v-col>
            <v-img
              v-if="pokemon.sprites !== undefined"
              :src="pokemon.sprites.front_default"
              aspect-ratio="1"
              contain
            ></v-img>
          </v-col>
          <v-col>
            <v-list class="transparent">
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title>Weight</v-list-item-title>
                  <v-list-item-subtitle>{{pokemon.weight/10}} kg.</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
              <v-list-item>
                <v-list-item-content>
                  <v-list-item-title>Height</v-list-item-title>
                  <v-list-item-subtitle>{{pokemon.height*10}} cm.</v-list-item-subtitle>
                </v-list-item-content>
              </v-list-item>
            </v-list>
          </v-col>
        </v-row>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script>
import axios from "axios";

export default {
  props: ["id"],
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
    console.log("this.id-->", this.id);
    const urlPokemon = `https://pokeapi.co/api/v2/pokemon/${this.id}/`;
    this.loadPokemon(urlPokemon);
  },
  methods: {
    loadPokemon(resource) {
      console.log(`Querying to resource: ${resource}`);

      // Connect to API: https://pokeapi.co/api/v2
      axios
        .get(resource)
        .then(response => {
          const { data } = response;
          console.log(data);

          if (data !== null && data !== undefined) {
            this.pokemon = data;
            const { sprites } = this.pokemon;

            if (sprites !== null && sprites !== undefined) {
              //   console.log("sprites", sprites);
              this.pokemonList = sprites;
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
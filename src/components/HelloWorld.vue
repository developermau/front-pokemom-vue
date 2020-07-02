<template>
  <div>
    <h1>Pokemons</h1>
    <v-container fluid>
      <v-row>
        <v-col cols="12" sm="6" md="4">
          <PokemonCard />
        </v-col>
        <v-col cols="12" sm="6" md="4">
          <PokemonCard />
        </v-col>
        <v-col cols="12" sm="6" md="4">
          <PokemonCard />
        </v-col>
        <v-col cols="12" sm="6" md="4">
          <PokemonCard />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import PokemonCard from "./PokemonCard";

export default {
  name: "HelloWorld",
  components: {
    PokemonCard
  }
};
</script>

<style lang="scss" scoped>
</style>
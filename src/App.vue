<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <h2>POKEDEX - "Coursera"</h2>
      <v-spacer></v-spacer>
      <v-btn to="/">Home</v-btn>
    </v-app-bar>
    <v-main>
      <v-container fluid>
        <router-view></router-view>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    //
  })
};
</script>

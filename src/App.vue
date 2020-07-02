<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <h1>POKEDEX - "Coursera"</h1>
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

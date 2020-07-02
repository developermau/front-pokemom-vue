<template>
  <v-container fluid>
    <h1 class="text-center">Pokemon {{id}}</h1>
    <v-row>
      <v-col cols="6" md="6">imagen</v-col>
      <v-col cols="6" md="6">text</v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  props: ["id"],
  created(){
      console.log("this.id-->", this.id)
  }
};
</script>

<style lang="scss" scoped>
</style>
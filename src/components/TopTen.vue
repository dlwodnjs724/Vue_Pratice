<template>
  <v-layout row wrap align-center>
    <v-flex v-for="(item, index) in top_ten">
      <v-card style="width:200px; min-height: 150px;">
        <a v-bind:href="item.link" style="text-decoration: none; color: black;" target="_blank"><v-card-text>{{index+1}}위<br />{{item.title}}</v-card-text></a>
        <!--{{item.title}}</v-card-text></a>-->
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
    export default {
        name: "TopTen",
      props: ["top_ten"]
    }
</script>

<style scoped>

</style>

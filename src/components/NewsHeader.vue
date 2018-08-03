<template>
  <v-carousel class="carousel" hide-delimiters="">
    <v-carousel-item v-for="list in topten">
      <news-flex v-bind:topfive="list"></news-flex>
    </v-carousel-item>
  </v-carousel>
</template>

<script>
  import NewsFlex from "./NewsFlex"
    export default {
      name: "NewHeader",
      components: { NewsFlex },
      props: [ "topten" ],
      data() {
        return {
        }
      }
    }
</script>

<style scoped>
  .carousel {
    height: 280px !important;
  }
</style>

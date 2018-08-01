<template>
  <v-layout row>
    <v-flex xs12>
      <v-text-field
        v-model= "keyword"
        label= "검색어를 입력하세요"
        v-on:keyup.enter="passkeyword"
      ></v-text-field>
    </v-flex>
    <v-flex p>
      <v-btn fab dark middle color="blue" v-on:click.stop="passkeyword">
        <v-icon dark style="padding-top: 15px">edit</v-icon>
      </v-btn>
    </v-flex>
  </v-layout>
</template>

<script>
    export default {
        name: "SearchBar",
      data() {
          return {
            keyword: ""
          }
      },
      methods: {
          passkeyword: function() {
            console.log("test");
            this.$emit('changekeyword', this.keyword);
            this.keyword = "";
          }
      }
    }
</script>

<style scoped>

</style>

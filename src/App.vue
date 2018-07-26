<template>
  <div id="app">
    <search-bar v-on:changekeyword="sendkeyword"></search-bar>
    <naver-list v-bind:top="tophun"></naver-list>
  </div>
</template>

<script>
// import Child from './components/Child'
import axios from 'axios'
import cleanstr from './add.js/cleanstring'
import NaverList from './components/NaverList'
import SearchBar from './components/SearchBar'
let clientId = "kzQ3ihXLZ9FKU_hnfqFM";
let clientSecret = "kE7iFJNaql";
export default {
  name: 'App',
  components: {
    // Child
    NaverList,
    SearchBar
  },
  data() {
    return {
      title: [],
      link: [],
      tophun: [],
      parentkeyword: "세종대"
    }
  },
  mounted() {
    this.search();
  },
  methods: {
    search: function () {
      axios({
        method: "get",
        url: "http://localhost:8080/naversearch",
        params: {
          query: this.parentkeyword,
          display: "100"
        },
        crossDomain: true,
        headers: {
          "X-Naver-Client-Id": clientId,
          "X-Naver-Client-Secret": clientSecret
        }
      }).then((result)=>{
        // console.log(result.data.items);
        let news = result.data.items;
        for (let i in news){
          var temp = {
            title: cleanstr(news[i].title, "title"),
            link: cleanstr(news[i].originallink, "link")
          }
          this.tophun.push(temp);
        }
      })
    },
    sendkeyword: function(val) {
      this.parentkeyword = val;
      this.tophun = [];
      this.search();
    }
  }
}
</script>

<style>

#app {

}
</style>

<template>
  <div id="app">

    <MyHeader @search="search" />
    <MyMain :movies="movies" :series="series" />

  </div>
</template>

<script>
//chiamata axios
import axios from "axios";

import MyHeader from "./components/MyHeader.vue";
import MyMain from "./components/MyMain.vue";

export default {
  name: "App",
  components: {
    MyHeader,
    MyMain,
  },
  data() {
    return {
      movies: [],
      series: [],
      api: {
        language: "it-IT",
        key: "1612beaf7a667a97d7e0e92a84e64df7",
        baseUri: "https://api.themoviedb.org/3",
      },
    };
  },
  methods: {
    search(searchText) {
      if (!searchText) {
        this.movies = [];
        this.series = [];
        return;
      }

      const { key, language } = this.api;

      const setting = {
        params: {
          language,
          api_key: key,
          query: searchText,
        },
      };
      this.callApi("search/movie", setting, "movies");
      this.callApi("search/tv", setting, "series");
    },
    callApi(endpoint, setting, pointer) {
      axios
        .get(`${this.api.baseUri}/${endpoint}`, setting)
        .then((res) => {
          this[pointer] = res.data.results;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style lang="scss">
@import "./assets/style/general.scss";

// importo font awesome metodo 2
// @import '~@fortawesome/fontawesome-free/css/all.css'

  body{
    background-color: #000;
  }

</style>
<template>
  <div id="app">
     
    <MyHeader @search="search"/>

  </div>
</template>

<script>
import axios from 'axios';

import MyHeader from './components/MyHeader.vue'

export default {
  name: 'App',
  components: {
    MyHeader,
  },
  data() {
    return{
      movies: [],
      api: {
        key: "1612beaf7a667a97d7e0e92a84e64df7",
        baseUri: "https://api.themoviedb.org/3/search/movie"
      }
    }
  },
  methods: {
    search(text) {
        if(!text) {
          this.movies = [];
          return;
        }

        const { key } = this.api;

        const setting = {
            values: {
              api_key: key,
              query: text,
            },
        };

        this.takeApi('search', setting, 'movies')

    },
    takeApi(endpoint, setting, pointer) {
      axios.get(`${ this.api.baseUri }/${ endpoint }`, setting).then((res) => {
        this[pointer] = res.data.results;
      })
      .catch((err) => {
        console.log(err)
      })
    }
  }
}
</script>

<style lang="scss">

  @import './assets/style/general.scss';

</style>

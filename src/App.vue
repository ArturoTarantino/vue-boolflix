<template>
  <div id="app">
    <Header @searchClicked="searchPerformed"/>
    <Main :requestItems="moviesList" :seriesRequest="seriesList" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data: function() {
    return {
      searchedText: '',
      moviesList: [],
      seriesList: []
    };
  },
  methods: {
    searchPerformed: function(text) {
      this.searchedText = text;
      this.getMovies();
      this.getSeries();
    },
    getMovies: function() {
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: '997df5abb3ca337fd1e2327f4dc80ef4',
          query: this.searchedText
        }
      })
      .then((response)=> {
        this.moviesList = response.data.results;
      });
    },
    getSeries: function() {
      axios.get('https://api.themoviedb.org/3/search/tv', {
        params: {
          api_key: '997df5abb3ca337fd1e2327f4dc80ef4',
          query: this.searchedText
        }
      })
      .then((response)=> {
        this.seriesList = response.data.results;
      });
    }
  }
};
</script>

<style lang="scss">
@import './style/general.scss';
@import './style/common.scss';

#app {
  width: 100%;
  height: 100vh;
}
</style>

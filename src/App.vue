<template>
  <div id="app">
    <Header @searchClicked="searchPerformed"/>
    <Main :moviesList="moviesList" :seriesList="seriesList" :popularMovies="popularMovies" :upcomingMovie="upcomingMovie" :checkLoad="isLoadingApi"/>
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
      apiKey: '997df5abb3ca337fd1e2327f4dc80ef4',
      searchedText: '',
      moviesList: [],
      seriesList: [],
      popularMovies: [],
      upcomingMovie: [],
      isLoadingApi: true
    };
  },
  methods: {
    searchPerformed: function(text) {
      this.searchedText = text;
      this.getMovies();
      this.getSeries();
      this.isLoadingApi = false;
    },
    getMovies: function() {
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: this.apiKey,
          query: this.searchedText,
          language: 'it-IT'
        }
      })
      .then((response)=> {
        this.moviesList = response.data.results;
      });
    },
    getSeries: function() {
      axios.get('https://api.themoviedb.org/3/search/tv', {
        params: {
          api_key: this.apiKey,
          query: this.searchedText,
          language: 'it-IT'
        }
      })
      .then((response)=> {
        this.seriesList = response.data.results;
      });
    }
  },
  created: function() {
    axios.get('https://api.themoviedb.org/3/movie/popular', {
      params: {
          api_key: this.apiKey,
          language: 'it-IT'
      }
    })
    .then((response)=>{
      this.popularMovies = response.data.results;
    });

    axios.get('https://api.themoviedb.org/3/movie/upcoming', {
      params: {
          api_key: this.apiKey,
          language: 'it-IT'
      }
    })
    .then((response)=>{
      this.upcomingMovie = response.data.results;
    });
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

<template>
  <div id="app">
    <Header />

    <!-- test  -->
    <div class="search-bar-test">
      <input v-model="searchedText" type="text" placeholder="inserisci il titolo del film">
      <button @click="callAPI" >cerca</button>
    </div>

    <Main :requestItems="requestItems" />
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
      requestItems: []
    };
  },
  methods: {
    // searchPerformed: function(text) {
    //   this.searchedText = text;
    // },
    callAPI: function() {
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: '997df5abb3ca337fd1e2327f4dc80ef4',
          query: this.searchedText
        }
      })
      .then((response)=> {
        this.requestItems = response.data.results;
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

  .search-bar-test {
    text-align: center;
    background-color: gray;
    padding-top: 10px;

    input {
      width: 300px;
      padding: 5px;
    }

    button {
      padding: 5px;
      font-weight: bold;
      text-transform: uppercase;
    }
  }
}
</style>

<template>
  <div>
    <Header 
      @search="getSearch"
    />
    <Main 
      :searchToMain="search"
    />
  </div>
</template>

<script>
import Header from "./components/Header"
import Main from "./components/Main"
import axios from "axios"


export default {
  name: 'App',

  components: {
    Header,
    Main
  },

  data(){
    return{
      searchFilm: "",
      search: []
    }
  },

  methods:{
    getSearch(film){
      this.searchFilm = film;
      axios.get("https://api.themoviedb.org/3/search/movie", {
        params:{
          api_key: "175c5ba4ca5c3e6fc669aa56a7f621e0",
          query : this.searchFilm
        }
      })
        .then( r => {
          this.search = r.data.results;
          console.log(r);
        })
        .catch( e => {
          console.log(e);
        });
    },
    
  }
}
</script>

<style lang="scss">
@import "./assets/style/vars.scss";
@import "./assets/style/utilities.scss";
@import "./assets/style/generals.scss"
</style>

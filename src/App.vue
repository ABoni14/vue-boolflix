<template>
  <div>
    <Header 
      @search="getSearch"
    />
    <Main 
      :searchToMain="searchFilm"
    />
  </div>
</template>

<script>
import Header from "./components/Header"
import Main from "./components/Main"


export default {
  name: 'App',

  components: {
    Header,
    Main
  },

  data(){
    return{
      searchFilm: "",
    }
  },

  methods:{
    getSearch(film){
      this.searchFilm = film
    }
  }
}
</script>

<style lang="scss">
@import "./assets/style/vars.scss";
@import "./assets/style/utilities.scss";
@import "./assets/style/generals.scss"
</style>

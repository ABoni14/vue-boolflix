<template>
  <main>
    <div class="container">
      <ul class="list">
        <li
        v-for="(film, index) in films"
        :key="index"
        >
          <h2>{{film.title}}</h2>
          <h3>{{film.original_title}}</h3>
          <p>{{film.original_language}}</p>
          <p>{{film.original_vote_average}}</p>
        </li>
      </ul>
    </div>
  </main>
</template>

<script>
import axios from "axios";

export default {
  name: "Main",

  data(){
    return{
      films: []
    }
  },

  props:{
    searchToMain: String
  },

  methods:{
    getApi(){
      axios.get("https://api.themoviedb.org/3/search/movie", {
        params:{
          api_key: "175c5ba4ca5c3e6fc669aa56a7f621e0",
          query : "terminator"
        }
      })
        .then( r => {
          this.films = r.data.results;
          console.log(r);
        })
        .catch( e => {
          console.log(e);
        });
    },
  },

   mounted(){
      this.getApi()
    }
}
</script>

<style lang="scss">
@import "../assets/style/vars.scss";

main{
  min-height: calc(100vh - 100px);
  background-color: grey;
  .list{
    display: flex;
    flex-wrap: wrap;
    list-style: none;
    li{
      margin: 10px;
      background-color: white;
      width: calc(100% / 5);
      padding: 20px;
    }
  }
}

</style>
<template>
  <main>
    <div class="container">
      <ul class="list">
        <li
        v-for="(film, index) in searchToMain"
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

export default {
  name: "Main",

  data(){
    return{
      string: ""
    }
  },

  props:{
    searchToMain: Array
  }
}
</script>

<style lang="scss">
@import "../assets/style/vars.scss";

main{
  min-height: calc(100vh - 100px);
  background-color: grey;
  padding: 30px 0;
  .list{
    display: flex;
    flex-wrap: wrap;
    list-style: none;
    li{
      margin: 10px;
      background-color: white;
      width: calc(100% / 5 - 20px);
      padding: 20px;
    }
  }
}

</style>
<template>
  <main>
    <div class="container">
      <div class="contain-card">
        <h2>FILM</h2>
        <Card 
        v-for="(film, index) in searchToMain"
        :key="index"
        :films="film"
        />
      </div>

      <div class="contain-card">
        <h2>SERIE TV</h2>
        <Card 
        v-for="(serie, index) in seriesMain"
        :key="index"
        :films="serie"
        />
      </div>
    </div>
  </main>
</template>

<script>
import Card from "./Card.vue";

export default {
  name: "Main",

  components:{
    Card
  },

  data(){
    return{
      string: ""
    }
  },

  props:{
    searchToMain: Array,
    seriesMain: Array
  }
}
</script>

<style lang="scss">
@import "../assets/style/vars.scss";

main{
  min-height: calc(100vh - 100px);
  background-image: linear-gradient(grey, lightgrey);
  padding: 30px 0;
  .contain.card{
    display: flex;
    flex-wrap: wrap;
  }
}

</style>
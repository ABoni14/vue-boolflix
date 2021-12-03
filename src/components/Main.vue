<template>
  <main>
    <div class="container">
      <div class="errorSearch"
      v-if="searchToMain.length <= 0 && seriesMain.length <= 0"
      >
        <h2 class="title">CERCA QUALCOSA</h2>
      </div>

      <div v-else class="contain">
        <div 
        class="contain-card"
        >
          <h2 class="title">FILM</h2>
          <Card 
          v-for="(film, index) in searchToMain"
          :key="index"
          :films="film"
          />
        </div>

        <div 
        v-if="seriesMain != []"
        class="contain-card">
          <h2 class="title">SERIE TV</h2>
          <Card 
          v-for="(serie, index) in seriesMain"
          :key="index"
          :films="serie"
          />
        </div>
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
  .title{
    padding-top: 40px;
    font-size: 45px;
  }
}

</style>
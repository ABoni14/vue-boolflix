<template>
<div class="flip-card ab-card">
  <div class="flip-card-inner">
    <div class="flip-card-front">
      <img 
      v-if="films.poster_path != null"
      :src="'http://image.tmdb.org/t/p/w342' + films.poster_path" alt="">
      <div v-else class="no-img">
          <h3 class="title" v-if="films.name">{{films.name}}</h3>
          <h3 class="title" v-else>{{films.title}}</h3>
          <h3 class="no-photo">Nessuna foto disponibile</h3>
      </div>
    </div>
    <div class="flip-card-back">
      <h2 v-if="films.name">Title: {{films.name}}</h2>
      <h2 v-else>Title: {{films.title}}</h2>

      <h3 v-if="films.original_name">Original title: {{films.original_name}}</h3>
      <h3 v-else>Original title: {{films.original_title}}</h3>

      <h4 
      v-if="films.original_language === 'en'">Language: <country-flag country='us' size='normal'/></h4>
      <h4 
      v-else-if="films.original_language === 'it'">Language: <country-flag country='it' size='normal'/></h4>
      <h4 
      v-else-if="films.original_language === 'cn'">Language: <country-flag country='cn' size='normal'/></h4>
      <h4 
      v-else-if="films.original_language === 'gb'">Language: <country-flag country='gb' size='normal'/></h4>
      <h4 
      v-else-if="films.original_language === 'es'">Language: <country-flag country='es' size='normal'/></h4>
      <h4 
      v-else>Language: {{films.original_language}}</h4>
      <h4 v-if="films.vote_average != 0">
        Vote: <i v-for="index in Math.floor(films.vote_average / 2)" :key="index" class="fas fa-star"></i>
      </h4>
      <h4 v-else>
        Vote: N/N
      </h4>
      <h4 v-if="films.overview !== ''">
        Overview: {{films.overview}}
      </h4>
      <h4 v-else>N/N</h4>
    </div>
  </div>
</div>
</template>

<script>
import CountryFlag from 'vue-country-flag';

export default {
name: "Card",

components:{
  CountryFlag,
},

props:{
  films: Object
},
}
</script>

<style lang="scss">
.flip-card {
  width: 300px;
  height: 450px;
  background-color: transparent;
  border: 1px solid #f1f1f1;
  perspective: 1000px;
  display: inline-block;
  margin: 10px;
  background-color: rgb(71, 71, 71);
  width: calc(100% / 4 - 20px);
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  img{
    overflow: hidden;
    object-fit: conver;
    height: 100%;
    width: 100%;
  }
  .no-img{
    height: 500px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    .title{
      margin-bottom: 30px;
      font-size: 25px;
    }
    .no-photo{
      font-size: 15px;
      color: rgb(19, 19, 19);
    }
  }
}

.flip-card-front {
  background-color: #bbb;
  color: black;
}

.flip-card-back {
  background-color: black;
  color: white;
  transform: rotateY(180deg);
  text-align: left;
  padding: 5px;
  overflow: auto;
  h2{
    font-size: 20px;
    margin-bottom: 15px;
  }
  h3{
    margin-bottom: 15px;
  }
  h4{
    margin-top: 20px;
  }
}
</style>
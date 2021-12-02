<template>
<div class="flip-card ab-card">
  <div class="flip-card-inner">
    <div class="flip-card-front">
      <img 
      v-if="films.poster_path != null"
      :src="'http://image.tmdb.org/t/p/w342' + films.poster_path" alt="">
      <h3 
      v-else class="no-img">Nessuna foto disponibile</h3>
    </div>
    <div class="flip-card-back">
      <h2 v-if="films.name">{{films.name}}</h2>
      <h2 v-else>{{films.title}}</h2>

      <h3 v-if="films.original_name">{{films.original_name}}</h3>
      <h3 v-else>{{films.original_title}}</h3>

      <h4 
      v-if="films.original_language === 'en'"><country-flag country='us' size='normal'/></h4>
      <h4 
      v-else-if="films.original_language === 'it'"><country-flag country='it' size='normal'/></h4>
      <h4 
      v-else-if="films.original_language === 'cn'"><country-flag country='cn' size='normal'/></h4>
      <h4 
      v-else-if="films.original_language === 'gb'"><country-flag country='gb' size='normal'/></h4>
      <h4 
      v-else-if="films.original_language === 'es'"><country-flag country='es' size='normal'/></h4>
      <h4 
      v-else>{{films.original_language}}</h4>

      <p
      v-if="films.vote_average != null"
      >{{films.vote_average}}</p>
      <p v-else>
        Voto: NN
      </p>
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
}
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
    line-height: 400px;
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
}
</style>
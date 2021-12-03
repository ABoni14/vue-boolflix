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
      <h4 v-if="films.name"><strong>Title: </strong>{{films.name}}</h4>
      <h4 v-else><strong>Title: </strong>{{films.title}}</h4>

      <h4 v-if="films.original_name"><strong>Original title: </strong>{{films.original_name}}</h4>
      <h4 v-else><strong>Original title: </strong>{{films.original_title}}</h4>

      <h4 
      v-if="films.original_language === 'en'"><strong>Language: </strong><country-flag country='us' size='normal'/></h4>
      <h4 
      v-else-if="films.original_language === 'it'"><strong>Language: </strong><country-flag country='it' size='normal'/></h4>
      <h4 
      v-else-if="films.original_language === 'cn'"><strong>Language: </strong><country-flag country='cn' size='normal'/></h4>
      <h4 
      v-else-if="films.original_language === 'gb'"><strong>Language: </strong><country-flag country='gb' size='normal'/></h4>
      <h4 
      v-else-if="films.original_language === 'es'"><strong>Language: </strong><country-flag country='es' size='normal'/></h4>
      <h4 
      v-else><strong>Language: </strong>{{films.original_language}}</h4>
      <h4 v-if="films.vote_average != number">
        <strong>Vote: </strong>
        <i 
        v-for="(intem, index) in 5" 
        :key="index" 
        class="fa-star"
        :class="index < Math.round(films.vote_average/2) ? 'fas' : 'far'"
        >
        </i>
      </h4>
      <h4 v-else>
        <strong>Vote: </strong>N/N
      </h4>
      <h4 v-if="films.overview != ''">
        <strong>Overview: </strong>{{films.overview}}
      </h4>
      <h4 v-else><strong>Overview: </strong> N/N</h4>
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
    height: 400px;
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
  h3{
    margin-bottom: 15px;
  }
  h4{
    margin-bottom: 20px;
    font-weight: normal;
    i{
      color: yellow;
    }
  }
}
</style>
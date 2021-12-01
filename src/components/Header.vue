<template>
  <header>
    <h1>BOOLFLIX</h1>
    <input 
    v-model="searchBar"
    @keyup.enter="$emit('search', search)"
    type="text" 
    placeholder="Cerca il film">
  </header>
</template>

<script>
export default {
  name: "Header",

  data(){
    return{
      searchBar: ""
    }
  },

  computed:{
    search(){
      return this.searchBar;
    }
  }
}
</script>

<style lang="scss">
header{
  height: 100px;
  background-color: black;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 25px;
  h1{
    color: red;
  }
  input{
    font-size: 20px;
    padding: 15px 30px;
  }
}
</style>
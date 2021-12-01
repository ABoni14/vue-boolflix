<template>
  <header>
    <h1>BOOLFLIX</h1>
    <input 
    v-model="searchBar"
    @keyup.enter="search"
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

  methods:{
    search(){
      this.$emit("search", this.searchBar);
      this.searchBar = "";
    }
  },

  mounted(){
    this.search()
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
<template>
  <header class="container">
    <h1>Pokedex</h1>
    <input type="text" placeholder="Search Pokemon" v-model="searchedWord" @keyup="search">
  </header>
</template>

<script>
export default {
    name: 'HeaderComponent',
    data(){
      return{
        searchedWord: ''
      }
    },
    methods: {
      search(){
        console.log(this.searchedWord);
        this.$emit('digit', this.searchedWord);
      }
    }
}
</script>

<style lang="scss" scoped>
  header{
    background-color: olive;
    text-align: center;
  }
</style>
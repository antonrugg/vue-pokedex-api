<template>
  <div id="app">
    
    <HeaderComponent @digit="doSearch" />
    <PokemonList :url="pokemonURL" :filterByName="searchPokemon" />
  </div>
</template>

<script>
import HeaderComponent from '@/components/HeaderComponent.vue'
import PokemonList from '@/components/PokemonList.vue'



export default {
  name: 'App',
  components: {
    HeaderComponent,
    PokemonList,
  },
  data() {
    return {
      pokemonURL: 'https:pokeapi.co/api/v2/pokemon',
      searchPokemon: '',
    }
  },
  methods: {
    doSearch(text){
      // console.log('App.vue ->', text);
      this.searchPokemon = text;
    }
  }
}
</script>

<style lang="scss">
@import '@/styles/general';


</style>

<template>
  <main class="container">
    <div class="row justify-content-between">
      <button @click="goPrevious" class="btn-primary col-6 w-25">
        Go Back
      </button>
      <button @click="goNext" class="btn-primary col-6 w-25">Next</button>
    </div>

    <div class="row">
      <div class="col-3" v-for="pokemon in filteredPokemons" :key="pokemon.id">
        <PokemonItem :pokemon="pokemon" :imageIndex="pokemon.id" />
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";
import PokemonItem from "@/components/PokemonItem.vue";

export default {
  name: "PokemonList",
  components: {
    PokemonItem,
  },
  props: {
    url: String,
    filterByName: String,
  },
  data() {
    return {
      pokemons: [],
      urlNext: '',
      urlPrevious: '',
      
    };
  },
  created() {
      this.queryPokemon(this.url);
  },
  computed: {
    filteredPokemons() {
      const pokemonWithId = this.pokemons.map((pokemon, index) => {
        return { ...pokemon, id: index };
      });

      const textToSearch = this.filterByName.toLowerCase().trim();

      if (!textToSearch) {
        return pokemonWithId;
      }

      return pokemonWithId.filter((pokemon) => {
        return pokemon.name.toLowerCase().includes(textToSearch);
      });
    },
  },
  methods: {
    goPrevious() {
      console.log("previous");
      this.queryPokemon(this.urlPrevious);
    },
    goNext() {
      console.log("next");
      this.queryPokemon(this.urlNext);
    },
    queryPokemon(url) {
        //baseUrl?limit=20
      axios
        .get(url, {
          params: {
            limit: 20,
          },
        })
        .then((response) => {
          if (response.status === 200 && response.data) {
            this.pokemons = response.data.results;
            console.log(this.response.data);
            this.urlNext = response.data.next;
            this.urlPrevious = response.data.previous;
          }
        })
        .catch((error) => {
          console.log("error", error);
        });
    },
  },
};
</script>

<style>
</style>
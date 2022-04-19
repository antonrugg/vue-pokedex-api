<template>
  <div class="card text-center ar-card">
      <img :src="pokemonImageUrl" :alt="pokemon.name">
      {{pokemon.name}}
  </div>
</template>

<script>
export default {
    name: 'PokemonItem',
    props: {
        pokemon: Object,
        imageIndex: Number,
    },
    data(){
        return{
            imageUrlBase: 'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/'
        }
    },
    mounted() {
        console.log(this.pokemon);
    },
    computed: {
        pokemonImageUrl(){
            return this.imageUrlBase + (this.imageIndex + 1) + '.png'
        }
    }
}
</script>

<style lang="scss" scoped>
    .ar-card{
        margin-top: 1rem;
        margin-bottom: 1rem;
        padding: 0.5rem;
        text-transform: uppercase;

        img{
            margin-bottom: 0.5rem;
        }
    }
</style>
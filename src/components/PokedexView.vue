<template>
  <div>
    <PokeHeaderView :discoveredCount="discoveredCount" />
    <div class="pokemon-container">
      <PokemonCardView
        v-for="pokemon in pokemons"
        :key="pokemon.name"
        :name="pokemon.name"
        :id="pokemon.id"
        :image="pokemonImage(pokemon.id)"
        @guess-correct="handleCorrectGuess(pokemon)"
      />
    </div>
  </div>
</template>

<script>
import axios from "axios";
import PokemonCardView from "./PokemonCardView.vue";
import PokeHeaderView from "./PokeHeaderView.vue";

export default {
  components: {
    PokemonCardView,
    PokeHeaderView,
  },
  data() {
    return {
      pokemons: [],
    };
  },
  mounted() {
    axios
      .get("https://pokeapi.co/api/v2/pokemon?limit=20")
      .then((response) => {
        this.pokemons = response.data.results.map((pokemon, index) => ({
          ...pokemon,
          id: index + 1,
          isDiscovered: false,
        }));
      })
      .catch((error) => console.error(error));
  },
  computed: {
    // contanding
    discoveredCount() {
      return this.pokemons.filter((pokemon) => pokemon.isDiscovered).length;
    },
  },
  methods: {
    handleCorrectGuess(pokemon) {
      pokemon.isDiscovered = true; // valida el pokemon descubierto
    },
    pokemonImage(id) {
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${id}.png`; // sprites de los pokemons
    },
  },
};
</script>

<style scoped>
.pokemon-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  max-width: 1200px;
}
</style>

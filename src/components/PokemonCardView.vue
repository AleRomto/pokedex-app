<template>
  <div :class="['pokemon-card', { expanded: isExpanded && !isDiscovered }]">
    <img
      :src="image"
      :class="{ blurred: !isDiscovered }"
      @click="expandCard"
      alt="Pokemon"
    />

    <div v-if="isExpanded && !isDiscovered" class="pokemon-guess">
      <input
        v-model="guess"
        @keyup.enter="checkGuess"
        placeholder="Escribe el nombre"
      />
      <button @click="checkGuess">Descubrir</button>
    </div>

    <p v-else-if="isDiscovered" class="pokemon-name">{{ name }}</p>
  </div>
</template>

<script>
export default {
  props: {
    name: String,
    id: Number,
    image: String,
  },
  data() {
    return {
      isExpanded: false,
      isDiscovered: false,
      guess: "",
    };
  },
  methods: {
    expandCard() {
      this.isExpanded = !this.isExpanded; //agranda la card un poquito para que sobresalga y aparezca con el input
    },
    checkGuess() {
      if (this.guess.toLowerCase() === this.name.toLowerCase()) {
        this.isDiscovered = true;
        this.isExpanded = false;
        this.$emit("guess-correct");
      } else {
        alert("Nombre incorrecto. Inténtalo de nuevo."); //alerta
      }
    },
  },
};
</script>

<style scoped>
.pokemon-card {
  border: 1px solid #ccc;
  padding: 10px;
  text-align: center;
  border-radius: 8px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
  transition: all 0.3s ease;
}

.pokemon-card img {
  width: 250px;
  height: 250px;
  object-fit: cover;
  cursor: pointer;
}

.pokemon-card.expanded {
  transform: scale(1.2);
  z-index: 10;
  position: relative;
}

.blurred {
  filter: blur(5px) grayscale(100%);
  transition: filter 0.3s ease;
}

.pokemon-guess {
  margin-top: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.pokemon-guess input {
  width: 150px;
  padding: 5px;
  border: 1px solid #000;
  border-radius: 4px;
}

.pokemon-guess button {
  margin-top: 10px;
  padding: 5px 10px;
  border: none;
  background-color: #ddd;
  cursor: pointer;
  border-radius: 4px;
}

.pokemon-name {
  font-size: 1.2em;
  font-weight: bold;
  margin-top: 10px;
}
</style>

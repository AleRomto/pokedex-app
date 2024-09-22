<template>
  <div id="app">
    <PokedexView />
  </div>
</template>

<script>
import PokedexView from "./components/PokedexView.vue";

export default {
  components: {
    PokedexView,
  },
};
</script>

<style>
body {
  background-color: #f0f0f0;
  font-family: "Arial", sans-serif;
}

#app {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  flex-direction: column;
}

h1 {
  color: #ff0000;
  text-shadow: 2px 2px 2px rgba(0, 0, 0, 0.3);
}

.pokemon-card {
  border: 2px solid #ff0000;
  border-radius: 10px;
  background-color: white;
  padding: 20px;
  margin: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  text-align: center;
}
</style>

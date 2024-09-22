<template>
  <header class="poke-header">
    <img
      src="https://1000marcas.net/wp-content/uploads/2020/01/Logo-Pokemon.png"
      alt="Pokémon Logo"
      class="poke-logo"
    />
    <!-- el logo puesto de forma muy ordinaria, perdón-->
    <h1 class="h1">¿Quién es ese Pokémon?</h1>
    <p>Pokémons descubiertos: {{ discoveredCount }}</p>
  </header>
</template>

<script>
export default {
  props: ["discoveredCount"],
};
</script>

<style scoped>
.poke-header {
  background-color: #ff0000;
  color: white;
  padding: 20px;
  text-align: center;
  border-radius: 10px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
}

.h1 {
  color: white;
}

.poke-logo {
  width: 150px;
  margin-bottom: 10px;
}
</style>

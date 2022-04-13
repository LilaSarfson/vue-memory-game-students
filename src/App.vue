<script setup>
// Importamos el JSON. Vue ya lo convierte en un array de objetos y lo poe en la variable pokedex
import pokedex from "./assets/pokedex.json";
import backCard from "./assets/back-card.png";
import RadialProgress from "vue3-radial-progress";
import Card from "./components/Card.vue";
import ChessBoard from "./components/ChessBoard.vue";
let pokeArray = pokedex.slice(0, 10);

let pokeArraySaneado = pokeArray.map(function (e) {
  return {
    id: e.id,
    name: e.name.english,
    img: `/pokemons/${e.id.toString().padStart(3, 0)}.png`,
  };
});
</script>

<template>
  <header>
    <h1>¡PokeMemory!</h1>
    <h2>Score:</h2>
    <RadialProgress
      :diameter="200"
      :completed-steps="completedSteps"
      :total-steps="totalSteps"
    >
      <!-- Your inner content here -->
    </RadialProgress>
  </header>

  <main>
    <ChessBoard :cards="pokeArray" :backCardImage="backCard" />
  </main>
</template>

<style>
</style>

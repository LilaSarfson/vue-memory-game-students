<script setup>
// Importamos el JSON. Vue ya lo convierte en un array de objetos y lo poe en la variable pokedex
import pokedex from "./assets/pokedex.json";
import backCard from "./assets/back-card.png";
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
pokeArray = pokeArraySaneado;
</script>

<template>
  <header>
    <h1>¡PokeMemory!</h1>
  </header>

  <main>
    <ChessBoard :cards="pokeArray" :backCardImage="backCard" />
  </main>
</template>

<style>
@import "./assets/base.css";

@media (hover: hover) {
  a:hover {
    background-color: hsla(160, 100%, 37%, 0.2);
  }
}

@media (min-width: 1024px) {
  body {
    display: flex;
  }
}
</style>

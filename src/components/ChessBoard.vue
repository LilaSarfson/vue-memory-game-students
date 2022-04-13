<!-- ChessBoard Component -->
<script setup>
import Card from "./Card.vue";
const props = defineProps({
  cards: Array,
  backCardImage: String,
});
</script>
<template>
  <div>
    <Card
      v-for="card in cards"
      :key="card.id"
      :back="backCardImage"
      :front="card.img"
      :reveal="false"
    ></Card>
    <Card
      v-for="card in cards"
      :key="card.id"
      :back="backCardImage"
      :front="card.img"
      :reveal="false"
    ></Card>
  </div>
</template>
<style>
div {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
  row-gap: 2rem;
}
</style>
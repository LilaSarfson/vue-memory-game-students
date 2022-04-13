<!-- ChessBoard Component -->
<script setup>
import Card from "./Card.vue";
import { reactive } from "vue";
const props = defineProps({
  cards: Array,
  backCardImage: String,
});
const cardsDoubled = props.cards.concat(props.cards);
let selectedCards = [];
console.log(cardsDoubled);
const cardsChessBoard = reactive(
  cardsDoubled.map((card) => {
    return {
      ...card,
      reveal: false,
    };
  })
);
function onCardClicked(card) {
  if (card.reveal) {
    return;
  }
  card.reveal = true;

  selectedCards.push(card);

  if (selectedCards.length == 2) {
    if (selectedCards[0].id !== selectedCards[1].id) {
      selectedCards[1].reveal = false;
      selectedCards[0].reveal = false;
    }
    selectedCards = [];
  }
  //   // Filtramos solo las que tienen el estado reveal
  //   const cardsRevealed = cardsChessBoard.filter((card) => card.reveal);
  //   const numCardsRevealed = cardsRevealed.length;

  //   // Hemos seleccionado un número par de cartas?
  //   if (numCardsRevealed % 2 == 0) {
  //     // comprobamos la última con la penúltima
  //     if (
  //       cardsRevealed[numCardsRevealed - 1].id ==
  //       cardsRevealed[numCardsRevealed - 2].id
  //     ) {
  //       console.log("Son correctas");
  //     }
  //   }
}
</script>
<template>
  <div>
    <Card
      @click="onCardClicked(card)"
      v-for="card in cardsChessBoard"
      :key="card.id"
      :back="backCardImage"
      :front="card.img"
      :reveal="card.reveal"
    ></Card>
  </div>
</template>
<style scoped>
div {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
  row-gap: 2rem;
}
</style>
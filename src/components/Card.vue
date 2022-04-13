<!-- Card Component -->
<script setup>
const props = defineProps({
  back: String,
  front: String,
  reveal: Boolean,
});
</script>
<template>
  <img v-if="reveal" :src="front" alt="pokeCard" />
  <img v-else :src="back" alt="pokemonButterfly" />
</template>

<style>
img {
  width: clamp(100px, 18vw, 175px);
}
</style>

<template>
  <main>
    <card-deck class="card-deck"></card-deck>
  </main>
</template>

<script>
import CardDeck from "../components/CardDeck.vue";

export default {
  components: { CardDeck },
};
</script>

<style scoped>
.card-deck {
  margin-left: auto;
  margin-right: auto;
  display: table;
  top: 30px;
}
</style>

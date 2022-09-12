<template>
  <main>
    <loading-spinner
      v-if="loading"
      :size="size + 1"
      :loaded="loaded"
    ></loading-spinner>
    <card-deck v-if="!loading" class="card-deck"></card-deck>
  </main>
</template>

<script>
import cards from "../assets/cards.json";
import CardDeck from "../components/CardDeck.vue";
import LoadingSpinner from "@/components/LoadingSpinner.vue";

export default {
  components: { CardDeck, LoadingSpinner },
  data() {
    return {
      cards: cards,
      size: cards.length,
      loaded: 0,
    };
  },
  mounted() {
    this.loadAssets();
  },
  methods: {
    loadAssets() {
      const self = this;
      const verso = new Image();
      verso.onload = () => {
        self.loaded++;
      };
      verso.src = require("@/assets/cards/verso.png");
      for (let id in this.cards) {
        const recto = new Image();
        recto.onload = () => {
          self.loaded++;
        };
        recto.src = require("@/assets/cards/rectos/" +
          this.cards[id].type +
          ".png");
      }
    },
  },
  computed: {
    loading() {
      return this.loaded < this.size;
    },
  },
};
</script>

<style scoped>
.card-deck {
  margin-left: auto;
  margin-right: auto;
  display: table;
  top: 30px;
}

.loading {
  background: transparent
    url("https://miro.medium.com/max/882/1*9EBHIOzhE1XfMYoKz1JcsQ.gif") center
    no-repeat;
  height: 400px;
  width: 400px;
}
</style>

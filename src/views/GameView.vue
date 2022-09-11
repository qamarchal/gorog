<template>
  <main>
    <card-deck v-if="!loading" class="card-deck"></card-deck>
  </main>
</template>

<script>
import CardDeck from "../components/CardDeck.vue";

export default {
  components: { CardDeck },
  data() {
    return {
      loading: true,
    };
  },
  mounted() {
    const self = this;
    const img = new Image();
    img.onload = () => {
      self.loading = false;
    };
    img.src = require("@/assets/cards/verso.png");
    setTimeout(function () {
      self.loading = false;
    }, 3000);
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

<template>
  <div @click.prevent="onClick">
    <reload-button></reload-button>
    <div v-for="(card, index) in cards" :key="card.id">
      <Transition name="slide">
        <card-flip
          :language="language"
          :type="card.type"
          :index="index"
          :ref="'card-' + card.id"
          :cardId="card.id"
          :style="'z-index:' + (index + 1)"
          :show="index > top - 2 || index % 8 == 7"
          v-if="deal > index / 8 && index <= top"
        ></card-flip>
      </Transition>
    </div>
  </div>
</template>

<script>
import originals from "../assets/cards.json";
import CardFlip from "./CardFlip.vue";
import ReloadButton from "./ReloadButton.vue";

export default {
  name: "card-deck",
  components: { CardFlip, ReloadButton },
  props: {
    language: String,
  },
  data() {
    return {
      originals: originals,
      deal: 0,
      top: 0,
      clickable: false,
      flip: true,
      cards: [],
    };
  },
  mounted() {
    shuffle(this.originals);
    this.cards = this.originals;
    var self = this;
    for (let i = 0; i < 4; i++) {
      setTimeout(function () {
        self.deal++;
      }, i * 400);
    }
    setTimeout(function () {
      self.clickable = true;
    }, 1600);
    // this.clickable = true;
    // this.deal = 4;
    this.top = this.cards.length - 1;
  },
  methods: {
    onClick() {
      if (!this.clickable) {
        return;
      }
      this.clickable = false;
      const topId = this.cards[this.top].id;
      const topRef = "card-" + topId;
      const topCard = this.$refs[topRef][0];
      topCard.onClick();
      if (topCard.close) {
        this.top--;
      }
      const self = this;
      setTimeout(function () {
        self.clickable = true;
      }, 200);
    },
  },
  computed: {},
};

function shuffle(array) {
  let index = array.length,
    randomIndex;

  while (index != 0) {
    randomIndex = Math.floor(Math.random() * index);
    index--;
    [array[index], array[randomIndex]] = [array[randomIndex], array[index]];
  }

  return array;
}
</script>

<style scoped></style>

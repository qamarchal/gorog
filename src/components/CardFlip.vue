<template>
  <div v-if="!close" class="card-wrapper" v-bind:class="{ grabbed: grabbed }">
    <Transition name="slide">
      <div :style="position">
        <div class="card" v-bind:class="{ flipped: flipped }">
          <card-verso :show="show" class="card-face card-verso" />
          <card-recto :show="show" class="card-face card-recto" :type="this.type" />
        </div>
        <!-- <div class="debug-id">{{ cardId }}</div> -->
        <!-- <div class="debug-index">{{ index }}</div> -->
      </div>
    </Transition>
  </div>
</template>

<script>
import CardRecto from "../components/CardRecto.vue";
import CardVerso from "../components/CardVerso.vue";

export default {
  name: "card-flip",
  props: {
    type: String,
    index: Number,
    cardId: String,
    show: Boolean
  },
  components: { CardRecto, CardVerso },
  data() {
    return {
      close: false,
      flipped: false,
      grabbed: false,
      clickable: true,
    };
  },
  methods: {
    onClick() {
      if (!this.clickable) {
        return;
      }
      this.clickable = false;
      if (!this.flipped) {
        this.flipped = true;
      } else {
        this.close = true;
      }
      this.grabbed = true;
      var self = this;
      setTimeout(function () {
        self.grabbed = false;
        self.clickable = true;
      }, 200);
    },
  },
  computed: {
    position() {
      return `
        padding-left: ${this.index / 2}px;
        padding-bottom: 0.5px;
      `;
    },
  },
};
</script>

<style scoped>
/* .slide-enter-active {
  transition: transform 0.7s;
  transform: translate(2000px, 500px);
}

.slide-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
} */

/* .slide-enter-from {
  transform: translate(-2000px, 500px);
} */
.slide-leave-to {
  transition: transform 0.7s;
  transform: translate(2000px, 500px);
}

.debug-id {
  position: absolute;
  right: 280px;
}
.debug-index {
  position: absolute;
  right: 30px;
}

/* 
.scene {
  width: 200px;
  height: 260px;
  border: 1px solid #ccc;
  margin: 40px 0;
  perspective: 600px;
} */

.card-wrapper {
  /* display: flex; */
  width: 350px;
}

.card {
  /* width: 350px; */
  /* text-align: center; */
  /* width: fit-content; */
  transition: transform 0.3s;
  transform-style: preserve-3d;
  cursor: pointer;
  position: relative;
  backface-visibility: hidden;
  /* left: calc(50% - 175px); */
  /* border: solid orange; */
  /* display: block; */
  /* border-width: 1px; */
}

.card-face {
  position: absolute;
  width: 100%;
  /* height: 100%; */
  line-height: 260px;
  color: white;
  text-align: center;
  font-weight: bold;
  font-size: 40px;
  backface-visibility: hidden;
  /* border: solid red;
  border-width: 10px; */
}

.card-recto {
  transform: rotateY(180deg);
  /* border: solid blue;
  border-width: 10px; */
}

.flipped {
  transition-delay: 0.1s;
  /* transition: transform 0.2s; */
  transform: rotateY(180deg);
}

.grabbed {
  transform: scale(1.2);
}

.card-wrapper {
  transition: transform 0.7s;
}
</style>

<template>
  <div class="card-image">
    <img v-if="show" :src="cover(src)" rel="preload" />
  </div>
</template>

<script>
export default {
  name: "card-image",
  props: {
    src: String,
    show: Boolean,
  },
  methods: {
    cover(url) {
      return require("@/assets/cards/" + url);
    },
  },
};
</script>

<style scoped>
.card-image {
  height: 426px;
  width: 300px;
  background-color: black;
  border-radius: 3% 3% 3% 3%;
  color: hsl(300, 50%, 95%);
  border-left: 1px solid hsl(40, 1%, 55%);
  border-bottom: 1px solid hsl(40, 1%, 15%);
  border-radius: 3% 3% 3% 3%;
}

img {
  width: 300px;
  border-radius: 3% 3% 3% 3%;
  background: linear-gradient(hsl(40, 1%, 52%), hsl(40, 1%, 10%));
}
</style>

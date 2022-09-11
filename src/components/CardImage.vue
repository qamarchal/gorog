<template>
  <!-- <div class="card-image"> -->
  <img :src="cover(src)" />
  <!-- </div> -->
</template>

<script>
export default {
  name: "card-image",
  props: {
    src: String,
  },
  methods : {

cover(url) {
  return require('@/assets/cards/' + url);
}

  }
};
</script>

<style scoped>
img {
  width: 300px;
  /* height:500px; */
  /* border-radius: 3%;
  border: solid darkgray;
  border-width: 0 0 0px 1px; */

  background: linear-gradient(hsl(40, 1%, 52%), hsl(40, 1%, 10%));
  /* text-align: center; */
  color: hsl(300, 50%, 95%);
  border-left: 1px solid hsl(40, 1%, 55%);
  border-bottom: 1px solid hsl(40, 1%, 15%);
  border-radius: 3% 3% 3% 3%;
  /* padding: 2rem 0.5rem; */
  /* background: linear-gradient(
      130deg,
      rgba(171, 17, 51, 1) 30%,
      rgba(255, 51, 102, 0.75)
    ),
    linear-gradient(200deg, #ab1133 50%, #ff3366 50%); */
}
</style>

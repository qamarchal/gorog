<template>
  <div class="card">
    <card-image :show="show" :src="'big.jpg'" />
  </div>
</template>

<script>
import CardImage from "./CardImage.vue";

export default {
  components: { CardImage },
  name: "card-verso",
  props:{
    show: Boolean
  }
};
</script>

<template>
  <div class="card">
    <card-image :show="show" :src="'verso.png'" />
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

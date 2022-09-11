<template>
  <div class="card">
    <card-image :show="show" :src="'rectos/' + type + '.png'" />
  </div>
</template>

<script>
import CardImage from "./CardImage.vue";

export default {
  components: { CardImage },
  name: "card-recto",
  props: {
    type: String,
    show: Boolean
  },
};
</script>

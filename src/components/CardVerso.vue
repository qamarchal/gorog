<template>
  <div class="card">
    <card-image :src="'verso.png'" />
  </div>
</template>

<script>
import CardImage from "./CardImage.vue";

export default {
  components: { CardImage },
  name: "card-verso",
};
</script>

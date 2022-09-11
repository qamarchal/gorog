<template>
  <div class="reload-button" @click="onClick"></div>
</template>

<script>
export default {
  name: "reload-button",
  data() {},
  methods: {
    onClick() {
      location.reload();
    },
  },
};
</script>

<style scoped>
* {
  height: 426px;
  width: 300px;
  cursor: pointer;
}

.reload-button {
  left: calc(50% - 150px);
  position: absolute;
  z-index: 0;
  text-decoration: none;
}
</style>

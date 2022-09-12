<template>
  <div class="loading-spinner">Loading assets {{ loaded }}/{{ size }}</div>
</template>

<script>
export default {
  name: "loading-spinner",
  props: {
    loaded: Number,
    size: Number,
  },
};
</script>

<style scoped>
.loading-spinner {
  margin-left: -15px;
  margin-top: 100px;
}
</style>

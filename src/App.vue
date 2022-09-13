<template>
  <GameView />
</template>

<script>
import GameView from "./views/GameView.vue";

export default {
  name: "App",
  components: {
    GameView,
  },
};
</script>

<style>
#app {
  font-size: 22px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #647c93;
  margin-top: 60px;
  -webkit-tap-highlight-color: rgba(255, 255, 255, 0);
  min-height: 100%;
  min-width: 100%;
  position: absolute;
  overflow: hidden;
}

body {
  background-color: rgb(23, 31, 40);
  overscroll-behavior-y: contain;
}
</style>

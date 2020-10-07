<template>
  <div id="app">
    <img alt="" src="" />
    <RandomCat msg="Random  Gif Cat" />
  </div>
</template>

<script>
import RandomCat from "./components/RandomCat.vue";

export default {
  name: "App",
  components: {
    RandomCat,
  },
};
</script>

<style>
body {
  background-color: #c1eafd;
}
#app {
  font-family: "Bebas Neue", cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

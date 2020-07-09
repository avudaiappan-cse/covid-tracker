<template>
  <div id="app">
    <MainPage />
  </div>
</template>

<script>
import MainPage from "./components/MainPage.vue";

export default {
  name: "App",
  components: {
    MainPage
  }
};
</script>

<style>
#app {
  padding: 0;
  margin: 0;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
  color: #2c3e50;
  background: #212121;
}
</style>

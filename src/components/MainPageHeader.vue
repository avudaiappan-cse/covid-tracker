<template>
  <header class="header">
    <h2>{{title}}</h2>
  </header>
</template>

<script>
export default {
  name: "Header",
  props: {
    title: String,
    count: Number
  }
};
</script>

<style scoped>
.header {
  padding: 1rem;
  background-color: #212121;
  color: white;
}
</style>
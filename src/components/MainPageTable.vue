<template>
  <tr>
    <td>{{region}}</td>
    <td>{{confirmed}}</td>
    <td>{{recovered}}</td>
    <td>{{deceased}}</td>
  </tr>
</template>

<script>
export default {
  name: "TableData",
  props: ["region", "recovered", "deceased", "confirmed"]
};
</script>

<style scoped>
td:nth-child(3) {
  color: limegreen;
}
td {
  padding: 0.2rem;
  text-align: center;
}
td:nth-child(4) {
  color: red;
}
tr {
  background-color: #212121;
  color: white;
  border-style: hidden;
}
tr:nth-child(odd) {
  background-color: #2e2e2e;
}
</style>
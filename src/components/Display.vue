<template>
  <div class="display">{{display}}</div>
</template>

<script>
export default {
  name: "Display",
  props: ["display"]
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.display {
  grid-column: col / span 3;
  grid-row: row;
  background-color: #ddd;
  color: #222;
  border-radius: 5px;
  padding: 20px;
  font-size: 150%;
  text-align: right;
}
</style>

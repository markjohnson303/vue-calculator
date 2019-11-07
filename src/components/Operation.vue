<template>
  <button>{{operation}}</button>
</template>

<script>
export default {
  name: "Operation",
  props: {
    operation: String
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>

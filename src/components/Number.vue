<template>
  <button>{{number}}</button>
</template>

<script>
export default {
  name: "Number",
  props: {
    number: Number
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>

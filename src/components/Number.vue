<template>
  <button class="button number" @click="$emit('number-input', number)">{{number}}</button>
</template>

<script>
export default {
  name: "Number",
  props: ["number"]
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.number {
  background-color: #444;
}
</style>

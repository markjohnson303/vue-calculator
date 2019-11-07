<template>
  <div>
    <p>Calculator</p>
    <Display></Display>
    <Number v-for="n in 10" :key="n" :number="10-n"></Number>
    <Operation operation="="></Operation>
  </div>
</template>

<script>
import Operation from "@/components/Operation.vue";
import Number from "@/components/Number.vue";
import Display from "@/components/Display.vue";
export default {
  name: "Calculator",
  components: {
    Number,
    Operation,
    Display
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>

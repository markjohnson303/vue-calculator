<template>
  <div>
    <p>Calculator</p>
    <Display></Display>
    <Button></Button>
  </div>
</template>

<script>
import Button from "@/components/Button.vue";
import Display from "@/components/Display.vue";
export default {
  name: "Calculator",
  components: {
    Button,
    Display
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>

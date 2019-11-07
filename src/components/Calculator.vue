<template>
  <div>
    <p>Calculator</p>
    <Display :display="display"></Display>
    <Number v-for="n in 10" :key="n" :number="10-n" @number-input="onNumberInput"></Number>
    <Number number="." @number-input="onNumberInput"></Number>
    <Operation operation="=" @operation-input="onOperationInput"></Operation>
    <Operation operation="+" @operation-input="onOperationInput"></Operation>
    <Operation operation="-" @operation-input="onOperationInput"></Operation>
    <Operation operation="*" @operation-input="onOperationInput"></Operation>
    <Operation operation="/" @operation-input="onOperationInput"></Operation>
  </div>
</template>

<script>
console.log(eval("2+2"));
import Operation from "@/components/Operation.vue";
import Number from "@/components/Number.vue";
import Display from "@/components/Display.vue";
export default {
  name: "Calculator",
  data: function() {
    return {
      display: "0"
    };
  },
  methods: {
    onNumberInput: function(number) {
      if (this.display === "0") {
        this.display = number.toString();
      } else {
        this.display += number;
      }
    },
    onOperationInput: function(operation) {
      if (operation === "=") {
        this.display = eval(this.display).toString();
      } else if (this.display != "0") {
        this.display += operation;
      }
    }
  },
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

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
    <Operation operation="C" @operation-input="onOperationInput"></Operation>
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
      display: "0",
      initialNumber: "",
      secondaryNumber: "",
      operation: ""
    };
  },
  methods: {
    onNumberInput: function(number) {
      if (!this.operation) {
        this.initialNumber += number.toString();
        this.display = this.initialNumber;
      } else {
        this.secondaryNumber += number.toString();
        this.display = this.secondaryNumber;
      }
    },
    onOperationInput: function(operation) {
      if (operation === "C") {
        this.display = "0";
        this.initialNumber = "";
        this.secondaryNumber = "";
        this.operation = "";
      } else if (operation === "=") {
        this.evaluateWithEquals();
      } else if (this.secondaryNumber) {
        this.evaluateWithOperation(operation);
      } else {
        this.operation = operation;
      }
    },
    evaluateWithEquals: function() {
      let result = eval(
        this.initialNumber + this.operation + this.secondaryNumber
      );
      this.display = result;
      this.initialNumber = result;
      this.secondaryNumber = "";
      this.operation = "";
    },
    evaluateWithOperation: function(operation) {
      let result = eval(
        this.initialNumber + this.operation + this.secondaryNumber
      );
      this.display = result;
      this.initialNumber = result;
      this.secondaryNumber = "";
      this.operation = operation;
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

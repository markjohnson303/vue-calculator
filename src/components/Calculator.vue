<template>
  <div class="wrapper">
    <Display :display="display"></Display>
    <Operation operation="C" @operation-input="onOperationInput"></Operation>
    <Number number="7" @number-input="onNumberInput"></Number>
    <Number number="8" @number-input="onNumberInput"></Number>
    <Number number="9" @number-input="onNumberInput"></Number>
    <Operation operation="/" @operation-input="onOperationInput"></Operation>
    <Number number="4" @number-input="onNumberInput"></Number>
    <Number number="5" @number-input="onNumberInput"></Number>
    <Number number="6" @number-input="onNumberInput"></Number>
    <Operation operation="*" @operation-input="onOperationInput"></Operation>
    <Number number="1" @number-input="onNumberInput"></Number>
    <Number number="2" @number-input="onNumberInput"></Number>
    <Number number="3" @number-input="onNumberInput"></Number>
    <Operation operation="-" @operation-input="onOperationInput"></Operation>
    <Number number="0" @number-input="onNumberInput"></Number>
    <Number number="." @number-input="onNumberInput"></Number>
    <Operation operation="=" @operation-input="onOperationInput"></Operation>
    <Operation operation="+" @operation-input="onOperationInput"></Operation>
  </div>
</template>

<script>
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
      } else if (operation === "=" || this.secondaryNumber) {
        this.evaluate(operation);
      } else {
        this.operation = operation;
      }
    },
    evaluate: function(invokingOperation) {
      let result = eval(
        this.initialNumber + this.operation + this.secondaryNumber
      );
      this.display = result;
      this.initialNumber = result;
      this.secondaryNumber = "";
      if (invokingOperation === "=") {
        this.operation = "";
      } else {
        this.operation = operation;
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
.wrapper {
  display: grid;
  grid-gap: 10px;
  grid-template-columns: [col] 75px [col] 75px [col] 75px [col] 75px;
  grid-template-rows: [row] auto;
  background-color: #e89d3a;
  color: #444;
  justify-content: center;
  width: 330px;
  border: 20px solid #e89d3a;
  border-radius: 25px;
  margin-left: auto;
  margin-right: auto;
}

.button {
  color: #fff;
  border-radius: 5px;
  padding: 20px;
  font-size: 150%;
  border: none;
  box-shadow: 5px 5px grey;
  transition-property: box-shadow;
  transition-duration: 0.2s;
}

button:focus {
  outline: 0;
}

button:active {
  box-shadow: 1px 1px grey;
}
</style>

<script setup>
import {ref} from 'vue';
import CalculatorRow from './components/CalculatorRow.vue';
import CalculatorDisplay from './components/CalculatorDisplay.vue';

const btn_content = ref([["C", "+/-", "%", "/"], [7, 8, 9, "x"], [4, 5, 6, "-"], [1, 2, 3, "+"], [0, ".", "="]])


const currentInput = ref("0") // default should be string
const secondInput = ref("") // secondInput is previous input
const answer = ref("")
const operator = ref("")

function displayText(e) {

  // string is expected
  // .textContent is a string
  let value = e.target.textContent
  let operatorList = ['+', '-', 'x', '/']

  if(currentInput.value === "0") {
    currentInput.value = ""
  }

  // reset button
  if(value === 'C') {
    currentInput.value = "0"
    secondInput.value = ""
    answer.value = ''
  }

  // turn currentInput into a percentage(decimal)
  if(value === '%') {
    currentInput.value = currentInput.value / 100
  }

  if(value === '+/-') {
    // console.log(typeof currentInput.value)
    currentInput.value > 0
    ? currentInput.value = (currentInput.value*-1).toString()
    : currentInput.value = Math.abs(currentInput.value).toString()
  }

  // max numbers to display is 9
  currentInput.value.length < 9
  && !isNaN(Number(value)) // true if value is a number
  ? currentInput.value = currentInput.value + value
  : null
  
  // no '.' yet then run ternary condition
  // concat '.' in currentInput
  !currentInput.value.toString().includes('.') && value === '.' ? currentInput.value = currentInput.value + value : null

  // check if value is in operatorList then set currentInput to ''
  // NOT YET DONE! NO COMMIT YET
  operatorList.forEach(op => {
    if(op === value) {
      // click operator btn then save currentInput to secondInput(previousInput) before setting currentInput to ""
      secondInput.value = currentInput.value    
      currentInput.value = ""
      // save value(an operator) to operator ref() then use operator.value for switch statements below
      operator.value = value
      // console.log("ref op: " + operator.value)
    }
  })

  if(value === "=") {
    switch(operator.value) {
      case "+":
        // secondInput as first operand
        // Saved the value of currentInput to secondInput
        // oper1 + oper2
        answer.value = Number(secondInput.value) + Number(currentInput.value)
        break
      case "-":
        answer.value = Number(secondInput.value) - Number(currentInput.value)
        break
      case "/":
        answer.value = Number(secondInput.value) / Number(currentInput.value)
        break
      case "x":
        answer.value = Number(secondInput.value) * Number(currentInput.value)
        break
    }

    // secondInput.value = answer.value
    currentInput.value = answer.value
    answer.value = ""
  }
}

</script>

<template>
  <div id="app">
    <CalculatorDisplay :txt="currentInput.toString()" :ans="answer.toString()" />
    <!-- passess btn_content as btn_list(prop)  -->
    <CalculatorRow :btn_list="btn_content" :display_txt="displayText" />
  </div>
</template>

<style scoped>
  #app {
    background: #222;
    padding: 0.8em 1em;
  }
</style>

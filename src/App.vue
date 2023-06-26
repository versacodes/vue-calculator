<script setup>
import {ref} from 'vue';
import CalculatorRow from './components/CalculatorRow.vue';
import CalculatorDisplay from './components/CalculatorDisplay.vue';

const btn_content = ref([["C", "+/-", "%", "/"], [7, 8, 9, "x"], [4, 5, 6, "-"], [1, 2, 3, "+"], [0, ".", "="]])


const currentInput = ref("")
const secondInput = ref("") // secondInput is previous input
const answer = ref("")
const operator = ref("")

function displayText(e) {
  
  let value = e.target.textContent
  let operatorList = ['+', '-', 'x', '/']

  // reset button
  if(value === 'C') {
    currentInput.value = ''
    answer.value = ''
  }

  // max numbers to display is 9
  currentInput.value.length < 9
  && !isNaN(Number(value))
  ? currentInput.value = currentInput.value + value
  : null
  
  // no '.' yet then run ternary condition
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

<script setup>
import {ref} from 'vue';
import CalculatorRow from './components/CalculatorRow.vue';
import CalculatorDisplay from './components/CalculatorDisplay.vue';

const btn_content = ref([["C", "+/-", "%", "/"], [7, 8, 9, "x"], [4, 5, 6, "-"], [1, 2, 3, "+"], [0, ".", "="]])

</script>

<template>
  <div id="app">
    <CalculatorDisplay />
    <!-- passess btn_content as btn_list(prop)  -->
    <CalculatorRow :btn_list="btn_content" />
  </div>
</template>

<style scoped>
  #app {
    background: #222;
    padding: 0.8em 1em;
  }
</style>

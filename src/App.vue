<script setup>
import {ref} from 'vue';
import CalculatorRow from './components/CalculatorRow.vue';

const btn_content = ref([["C", "+/-", "%", "/"], [7, 8, 9, "x"], [4, 5, 6, "-"], [1, 2, 3, "+"], [0, ".", "="]])

</script>

<template>
  <!-- passess btn_content as btn_list(prop)  -->
  <CalculatorRow :btn_list="btn_content" />
</template>

<style scoped>


</style>

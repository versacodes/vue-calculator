<script setup>
import {ref} from 'vue'
const button_contents = ref([["C", "+/-", "%", "/"], [7, 8, 9, "x"], [4, 5, 6, "-"], [1, 2, 3, "+"], [0, ".", "~", "="]])

</script>

<template>
  <div class="btn-row">
    <button class="calc-btn" v-for="elem in button_contents[0]">{{elem}}</button>
  </div>
  <div class="btn-row">
    <button class="calc-btn" v-for="elem in button_contents[1]">{{elem}}</button>
  </div>
  <div class="btn-row">
    <button class="calc-btn" v-for="elem in button_contents[2]">{{elem}}</button>
  </div>
  <div class="btn-row">
    <button class="calc-btn" v-for="elem in button_contents[3]">{{elem}}</button>
  </div>
  <div class="btn-row">
    <button class="calc-btn" v-for="elem in button_contents[4]">{{elem}}</button>
  </div>
</template>

<style scoped>

.btn-row ~ .btn-row {
  margin-top: 7px;
}

.calc-btn {
  background: #666;
  width: 60px;
  height: 60px;
  border-radius: 50%;
  display: inline-block;
  font-size: 18px;
}

.calc-btn:hover {
  background: #555;
}

.calc-btn ~ .calc-btn {
  margin-left: 5px;
}

</style>


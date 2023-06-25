<script setup>
import {ref} from 'vue'
const button_contents = ref(["C", "+/-", "%", 1])

</script>

<template>
  <div class="btn-row">
    <button class="calc-btn" v-for="index in 3">{{index}}</button>
  </div>
</template>

<style scoped>

.calc-btn {
  background: #666;
  width: 60px;
  height: 60px;
  border-radius: 50%;
  display: inline-block;
}

.calc-btn:hover {
  background: #555;
}

.calc-btn ~ .calc-btn {
  margin-left: 5px;
}

</style>


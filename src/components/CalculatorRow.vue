<script setup>
import {ref} from 'vue'

const props = defineProps({
  btn_list: Array
})

</script>

<template>
  <!-- loop using passed prop btn_list -->
  <div class="btn-row" v-for="row in btn_list">
    <button class="calc-btn" v-for="elem in row">{{ elem }}</button>
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


<script setup>
import { ref } from 'vue'
import { nanoid } from 'nanoid' 

const props = defineProps({
  btn_list: Array
})

// classCount() to add another class to .btn-row based on index(row#)
function classCount(number) {
  return "btn-row-" + number.toString()
}

// same as classCount but for .calc-btn
function btnCount(number) {
  return "calc-btn-" + number.toString()
}

</script>

<template>
  <!-- nested loop using passed prop btn_list -->
  <!-- no id, instead used nanoid() library -->
  <div class="btn-row" v-for="(row, index) in btn_list" :key="nanoid()" :class="classCount(index)">
    <!-- for styling, use target .btn-row-theRowNumber > .calc-btn-theNumber -->
    <button class="calc-btn" v-for="(elem, index) in row" :key="nanoid()" :class="btnCount(index)">{{ elem }}</button>
  </div>
</template>

<style scoped>

.btn-row ~ .btn-row {
  margin-top: 7px;
}

/* change background of a first .btn-row buttons except for the last one  */
.btn-row-0 :not(.calc-btn-3) {
  background: #448;
}

/* change background onhover of a first .btn-row buttons except for the last one  */
.btn-row-0 :not(.calc-btn-3):hover {
  background: #449;
}

/* change background of the last button of every .btn-row */
.btn-row :last-child {
  background: #f81;
}
/* change background onhover of the last button of every .btn-row */
.btn-row :last-child:hover {
  background: #f84;
}

.calc-btn {
  background: #555;
  width: 60px;
  height: 60px;
  border-radius: 50%;
  display: inline-block;
  font-size: 18px;
  text-align: center;
}

.calc-btn:hover {
  background: #777;
}

.calc-btn ~ .calc-btn {
  margin-left: 5px;
}

</style>


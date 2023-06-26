<script setup>
import { ref } from 'vue'
import { nanoid } from 'nanoid' 

const props = defineProps({
  btn_list: Array,
  display_txt: Function
})

// console.log(props.display_txt)

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
    <button type="button" class="calc-btn" v-for="(elem, index) in row" :key="nanoid()" :class="btnCount(index)" @click="display_txt">{{ elem }}</button>
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
  width: 50px;
  height: 50px;
  border-radius: 50%;
  display: inline-block;
  font-size: 14px;
  text-align: center;
  font-weight: bold;
}

.calc-btn:hover {
  background: #777;
}

.calc-btn ~ .calc-btn {
  margin-left: 5px;
}

</style>


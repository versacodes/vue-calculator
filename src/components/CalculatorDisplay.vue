<script setup> 
import { ref, onMounted, onBeforeUpdate } from 'vue'

// get .number-text element from DOM
const textEl = ref(null)

const props = defineProps({
  txt: String,
  ans: String
})

// console.log(props.txt)
// change fontsize if based on length
onBeforeUpdate(() => {
  if(props.txt.length > 9) {
    textEl.value.style.fontSize = "27px"
  }
  if(props.txt.length > 11) {
    textEl.value.style.fontSize = "29px"
  }
})

</script>

<template>
  <div class="display">
    <!-- if ans is false, show txt -->
    <div class="number-text" ref="textEl">{{ ans || txt }}</div>
  </div>
</template>


<style scoped>
  .display {
    background: #222;
    width: 100%;
    height: 120px;
    margin-bottom: 8px;
    position: relative;
  }
  .number-text {
    position: absolute;
    bottom: 0;
    text-align: right;
    /* background: #114; */
    width: 100%;
    /* height: 100%; */
    font-size: 34px;
    letter-spacing: 1.5px;
    overflow-wrap: break-word;
    /* padding: 0 2px; */
  }
  .number-text-small {
    font-size: 30px;
  }
</style>


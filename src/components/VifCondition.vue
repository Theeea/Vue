<script setup>
import {ref, onMounted, computed} from 'vue'

const type = ref("A")

const classControl = ref(true)
function classToggle() {
  classControl.value = !classControl.value;
}

const vShowControl = ref(true)
function showToggle() {
  vShowControl.value = !vShowControl.value;
}
</script>

<template>
  <div v-if="type === 'A'">
    A
  </div>
  <div v-else-if="type === 'B'">
    B
  </div>
  <div v-else>
    C
  </div>

  <div>
    <button @click="classToggle">Toggle</button>
    <div v-if="classControl">toggle</div>
    <button @click="showToggle">V-Show</button>
    <div v-if="vShowControl">v_show</div>
  </div>
</template>

<style scoped>

</style>
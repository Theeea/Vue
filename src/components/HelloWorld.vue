<script setup>
import { ref, onMounted } from 'vue'

defineProps({
  msg: String
})

const counter = ref(0)
onMounted(() => {
  setInterval(() => {
    counter.value++;
  }, 1000)
});
</script>

<template>
  <div id="counter">
    Counter: {{ counter }}
  </div>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
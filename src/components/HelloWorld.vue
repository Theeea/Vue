<script setup>
import {ref, onMounted} from 'vue'

defineProps({
  msg: String
})

const counter = ref(0)
onMounted(() => {
  setInterval(() => {
    counter.value++;
  }, 1000)
});

const message = ref('이 페이지를 다음 시간에 열었습니다. ' + new Date().toLocaleString())

</script>

<template>
  <div id="counter">
    Counter: {{ counter }}
  </div>

  <div id="bind-attribute">
  <span v-bind:title="message">
    여기에 마우스를 올려두고 잠시 기다리면 제목이 동적으로 바뀝니다!
  </span>
  </div>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
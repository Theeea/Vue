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
const input_message = ref('Hello Vue.js!')
const two_way_binding = ref('asdf')
function reverseMessage() {
  input_message.value = input_message.value.split('').reverse().join('')
}

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

  <div id="event-handling">
    <p>{{ input_message }}</p>
    <button v-on:click="reverseMessage">Reverse Message</button>
  </div>

  <div id="two-way-binding">
    <p>{{ two_way_binding }}</p>
    <input v-model="two_way_binding" />
  </div>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
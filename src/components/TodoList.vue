<script setup>
import {ref} from 'vue'
import TodoItem from "./TodoItem.vue";

const groceryList = ref([
  { id: 0, text: '야채' },
  { id: 1, text: '치즈' },
  { id: 2, text: '사람이 먹을수 있는거라면 뭐든지' }
])

</script>

<template>
  <ol>
    <!--
      이제 할일 todo-item 에 할일을 전달합니다.
      콘텐츠는 동적으로 포현됩니다.
      여기에서 "key"를 또 전달하고 있는데
      이것에 대해서는 나중에 설명하겠습니다.
    -->
    <todo-item
        v-for="item in groceryList"
        v-bind:todo="item"
        v-bind:key="item.id"
    ></todo-item>
  </ol>
</template>

<style scoped>

</style>
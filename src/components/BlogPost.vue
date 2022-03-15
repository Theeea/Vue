<script setup>
import { ref } from 'vue'
import Comp from './Comp.vue'
defineProps(['title', 'id'])

const contents = ref([
  { id: 1, content: '11111' },
  { id: 2, content: '22222' },
  { id: 3, content: '33333' },
])
</script>

<template>
  <h4>
    {{id}}: {{ title }}
    <button @click="$emit('enlarge-text')">글씨 크게</button>
    <button @click="$emit('reduce-text')">글씨 작게</button>
  </h4>
  <Comp v-for="content in contents"
        :content=content.content>
  </Comp>
</template>
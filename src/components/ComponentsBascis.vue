<script setup>
import {ref, onMounted, computed} from 'vue'

import Slot from "./sub/Slot.vue";
import BaseInput from "./sub/BaseInput.vue";

const input1 = ref('');
const input2 = ref('');
</script>

<template>
  커스텀이벤트로 작성 <base-input @custom="input1 = $event"></base-input>
  <p>{{ input1 }}</p>
  기본 이벤트객체 이용 <input :value="input2" @input="input2 = $event.target.value">
  <p>{{ input2 }}</p>
  <Slot>
    Slot Content
  </Slot>
</template>

<style scoped>

</style>

<script setup>
import {ref, onMounted, computed} from 'vue';

const message = ref("")
const checked = ref(false)
const checkedNames = ref([])
const selected_box = ref('')
const selected_radio = ref('')
const options = ref([
  { text: 'One', value: 'A' },
  { text: 'Two', value: 'B' },
  { text: 'Three', value: 'C' }
])
const selected_ = ref('A')
</script>

<template>
  <input v-model="message" placeholder="여기를 수정해보세요" />
  <p>메시지: {{ message }}</p>
  <textarea v-model="message" placeholder="여러줄을 입력해보세요"></textarea>
<br>
  <input type="checkbox" id="checkbox" v-model="checked" />
  <label for="checkbox">{{ checked }}</label>

  <div id="v-model-multiple-checkboxes">
    <input type="checkbox" id="jack" value="Jack" v-model="checkedNames" />
    <label for="jack">Jack</label>
    <input type="checkbox" id="john" value="John" v-model="checkedNames" />
    <label for="john">John</label>
    <input type="checkbox" id="mike" value="Mike" v-model="checkedNames" />
    <label for="mike">Mike</label>
    <br />
    <span>Checked names: {{ checkedNames }}</span>
  </div>

  <div id="v-model-select_box" class="demo">
    <select v-model="selected_box">
      <option disabled value="">Please select one</option>
      <option>A</option>
      <option>B</option>
      <option>C</option>
    </select>
    <span>Selected: {{ selected_box }}</span>
  </div>

  <div id="v-model-radiobutton">
    <input type="radio" id="one" value="One" v-model="selected_radio" />
    <label for="one">One</label>
    <br />
    <input type="radio" id="two" value="Two" v-model="selected_radio" />
    <label for="two">Two</label>
    <br />
    <span>Picked: {{ selected_radio }}</span>
  </div>

  <div id="v-model-select-dynamic" class="demo">
    <select v-model="selected_">
      <option v-for="option in options" :value="option.value">
        {{ option.text }}
      </option>
    </select>
    <span>Selected: {{ selected_ }}</span>
  </div>
</template>

<style scoped>

</style>
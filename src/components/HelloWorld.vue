<script setup>
import {ref, onMounted, computed} from 'vue'
import TodoList from './TodoList.vue'
import ComputedAndWatch from "./ComputedAndWatch.vue";
import StyleClass from "./StyleClass.vue";
import VifCondition from "./VifCondition.vue";
import ListRendering from "./ListRendering.vue";
import EventListner from "./EventListner.vue";
import FormBinding from "./FormBinding.vue";
import ComponentsBasic from "./ComponentsBascis.vue";
import BlogPost from './BlogPost.vue';
import DynamicComponent from './DynamicComponent.vue';

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
const is_true = ref(true)
const btn_message = ref('숨기기')
function changeStatus() {
  if (is_true.value === true) {
    btn_message.value = '표시하기'
    is_true.value = false
  }
  else {
    btn_message.value = '숨기기'
    is_true.value = true
  }
}
const todos = ref([
    {text: 'Learn JavaScript'},
    {text: 'Learn Vue'},
    {text: 'Build something awesome'}])

const author = ref([
  {
    name: '존 도우',
    books: [
      'Vue 2 - Advanced Guide',
      'Vue 3 - Basic Guide',
      'Vue 4 - The Mystery'
    ]
  }
])

const isPublished = computed({
  get: () => author.value[0].books.length > 0 ? '있음' : '없음',
})
// const publishedBooksMessage = computed(() => {
//   return author.books.length > 0 ? 'Yes' : 'No'
// })

const isActive = ref(true)
const test = ref(true)
const error = ref(null)
const classObject = computed(() => ({
  active: isActive.value, test: test.value, 'text-danger': error.value
}))

import { reactive } from 'vue'

const state = reactive({ count: 0 })

function increment() {
  state.count++
}

const obj = reactive({
  nested: { count: 0 },
  arr: ['foo', 'bar']
})

function mutateDeeply() {
  // these will work as expected.
  obj.nested.count++
  obj.arr.push('baz')
}

const posts = ref([
  { id: 1, title: 'My journey with Vue' },
  { id: 2, title: 'Blogging with Vue' },
  { id: 3, title: 'Why Vue is so fun' }
])

const postFontSize = ref(1)
</script>

<template>
  <button @click="mutateDeeply">
    {{ obj.nested.count }}
  </button>
  <button @click="increment">
    {{ state.count }}
  </button>
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

  <div id="conditional-rendering">
    <span v-if="is_true">이제 나를 볼수 있어요</span><br>
    <button class="button" v-on:click="changeStatus">{{btn_message}}</button>
  </div>

  <div id="list-rendering" class="demo">
    <ol>
      <li v-for="todo in todos">
        {{ todo.text }}
      </li>
    </ol>
  </div>
  <TodoList>

  </TodoList>

  <div id="computed-basics">
    <span>출판된 책: </span>
    <span>{{ isPublished }}</span>
  </div>

  <button v-on:click="changeActiveComponent">ComputedAndWatch</button>
  <ComputedAndWatch>

  </ComputedAndWatch>

  <div :class="classObject">asdf</div>

  <button v-on:click="changeActiveComponent">StyleClass</button>
  <StyleClass>

  </StyleClass>

  <VifCondition>

  </VifCondition>

  <ListRendering>

  </ListRendering>

  <EventListner>

  </EventListner>

  <p>
    폼 바인딩
  </p>
  <FormBinding>

  </FormBinding>

  <ComponentsBasic>

  </ComponentsBasic>

  <div :style="{ fontSize: postFontSize + 'em' }">
    <BlogPost
        v-for="post in posts"
        :id="post.id"
        :title="post.title"
        @enlarge-text="postFontSize += 0.1"
        @reduce-text="postFontSize -= 0.1">
    </BlogPost>
  </div>

  <DynamicComponent>

  </DynamicComponent>
</template>

<style scoped>
a {
  color: #42b983;
}
.demo {
  font-family: sans-serif;
  border: 1px solid #eee;
  border-radius: 2px;
  padding: 20px 30px;
  margin-top: 1em;
  margin-bottom: 40px;
  user-select: none;
  overflow-x: auto;
}

.demo li {
  width: 333px;
  margin: 0px;
  padding: 0px;
}

.button {
  width: 123px;
}

.text-danger {
  color: red;
}
</style>
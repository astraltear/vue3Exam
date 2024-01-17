<template>
 
<ExamVue0></ExamVue0> 
<examvue1></examvue1>
<exam-vue2></exam-vue2>
<ExamVue3></ExamVue3>
<ExamVue4></ExamVue4>
<ExamVue5></ExamVue5>


<ul>
  <li>

  </li>
</ul>
<ToDoItem></ToDoItem>
  
</template>

<script>

import examvue1  from './components/ExamVue1.vue'
import ExamVue2 from './components/ExamVue2.vue';
import ExamVue3 from './components/ExamVue3.vue';
import ExamVue4 from './components/ExamVue4.vue';
import ExamVue5 from './components/ExamVue5.vue';
import ExamVue0 from './components/ExamVue0.vue';

import {uniqueId} from "lodash";
import ToDoItem from './components/ToDoItem.vue';

export default {
  components: {
    ExamVue0,
    examvue1,
    ExamVue2,
    ExamVue3,
    ExamVue4,
    ExamVue5,
    ToDoItem,

  },
  data() {
    return {
      ToDoItems: [
        { id: uniqueId("todo-"), label: "Learn Vue", done: false },
        { id: uniqueId("todo-"), label: "Create a Vue project with the CLI", done: true },
        { id: uniqueId("todo-"), label: "Have fun", done: true },
        { id: uniqueId("todo-"), label: "Create a to-do list", done: false },
      ],
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>


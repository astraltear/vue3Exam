<template>
 
<ExamVue0></ExamVue0> 
<examvue1></examvue1>
<exam-vue2></exam-vue2>
<ExamVue3></ExamVue3>
<ExamVue4></ExamVue4>
<ExamVue5></ExamVue5>

<h1>ToDoSample</h1>
<ToDoForm @todo-added="addToDo"></ToDoForm>
<ul>
  <li v-for="item in ToDoItems" v-bind:key="item.id">
    <ToDoItem
      v-bind:id="item.id"
      v-bind:label="item.label" 
      v-bind:done="item.done"
      @checkbox-changed="updateDoneStatus"
      @item-deleted="deleteToDo(item.id)"
      @item-edited2="editToDo(item.id, $event)"
    ></ToDoItem>
  </li>
</ul>

<p>{{ ToDoItems.filter(it => it.done).length }} /{{ ToDoItems.length }}</p>
<p>{{ listSummary }}</p>
<p>event:::::{{ $event }}</p>
<hr>



</template>

<script>
/* eslint-disable no-unused-vars  */
import ExamVue0 from './components/ExamVue0.vue';
import examvue1  from './components/ExamVue1.vue'
import ExamVue2 from './components/ExamVue2.vue';
import ExamVue3 from './components/ExamVue3.vue';
import ExamVue4 from './components/ExamVue4.vue';
import ExamVue5 from './components/ExamVue5.vue';

import {uniqueId} from "lodash";
import ToDoItem from './components/ToDoItem.vue';
import ToDoForm from "./components/ToDoForm";



export default {
  components: {
    ExamVue0, examvue1, ExamVue2, ExamVue3, ExamVue4, ExamVue5,
    ToDoItem, ToDoForm,

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
  computed:{
    listSummary() {
      const numberFinishedItems = this.ToDoItems.filter((item) =>item.done).length;
      return `${numberFinishedItems} out of ${this.ToDoItems.length} items completed`;
    }
  },
  methods: {
    updateDoneStatus(obj){
      console.log("updateDoneStatus::"+obj.uid);
      const item = this.ToDoItems.find((it) => it.id = obj.uid );
      item.done = !item.done;
    },
    addToDo(newLable){
      console.log("Todo added:::",newLable);
      this.ToDoItems.push({id:uniqueId("todo-"), label: newLable, done: false})
    },

    deleteToDo(toDoId) {
      const itemIndex = this.ToDoItems.findIndex((item) => item.id === toDoId);
      this.ToDoItems.splice(itemIndex, 1);
    },
    editToDo(toDoId, newLabel) {
      console.log("editToDo.newLabel:"+newLabel);
      const toDoToEdit = this.ToDoItems.find((item) => item.id === toDoId);
      toDoToEdit.label = newLabel;
    },

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


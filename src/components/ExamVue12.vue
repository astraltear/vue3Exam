<template>
  <form @submit.prevent="addTodo">
    <input v-model="state.newTodo">
    <button>add TODO</button>
  </form>
  <div>
    <li v-for="t in state.todos">
      {{ t }}
      <button @click="removeTodo(t)">X</button>
    </li>
  </div>
</template>

<script>
import { reactive } from 'vue'

export default {
  setup () {

    var id=0;

    const state = reactive({
      newTodo : '',
      todos : [
              { id: id++, text: 'HTML' },
              { id: id++, text: 'JavaScript' },
              { id: id++, text: 'Vue' }
            ],
    })

    function addTodo() {
      this.state.todos.push({ id: id++, text: state.newTodo })
      console.log(this.state.todos)
      state.newTodo="";
       
    }
    
    function removeTodo(todo){
      this.state.todos =  this.state.todos.filter( (t) => t !== todo  )
    }
  
    return {
      state,  addTodo,  removeTodo,
    }
  }
}
</script>
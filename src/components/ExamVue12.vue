<template>
  <form @submit.prevent="addTodo">
    <input v-model="state.newTodo">
    <button>add TODO</button>
  </form>
  <div>
    <li v-for="t in filterdTodos">
      <input type="checkbox" v-model="t.done">
      {{ t }}
      <button @click="removeTodo(t)">X</button>
    </li>
  </div>
  <div>
    <button @click="hideCompleted = !hideCompleted"> {{ hideCompleted ? 'Show all' : 'Hide completed' }} </button>
  </div>

  
</template>

<script>
import { reactive, computed,ref, watch,  } from 'vue'

export default {
  setup () {
    var id=0;

    const hideCompleted=ref(false);
    const state = reactive({
      newTodo : '',      
      todos : [
              { id: id++, text: 'HTML'  , done:false },
              { id: id++, text: 'JavaScript' , done:true },
              { id: id++, text: 'Vue' , done:false }
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

    const filterdTodos =  computed( () => {
      console.log("computed");
      return hideCompleted.value ? state.todos.filter( (t) => !t.done ) : state.todos ;
    })

    // hideCompleted가 변경될 때마다   watch가 호출되고 computed 함수가 다시 실행
    const watchFilterTodos = watch( hideCompleted, () => { 
      console.log("watch:", hideCompleted);
      /*
      watch 함수는 일반적으로 리턴을 하지 않습니다. 
      watch 함수는 특정 데이터의 변경을 감지하고 그에 따라 특정 동작을 수행하기 위한 것

      특정 데이터의 변경을 감지하여 그에 따른 값 변화를 적용하고 싶다면, 
      해당 데이터를 ref로 감싸서 computed 속성을 사용하는 것이 좋습니다. 
      computed는 종속된 데이터가 변경될 때 자동으로 호출되며, 그 결과 값을 리턴
      */
      // return hideCompleted.value ? state.todos.filter( (t) => !t.done ) : state.todos ;
    })
  
    return {
      state,  addTodo,  removeTodo,filterdTodos,hideCompleted, watchFilterTodos,
    }
  }
}
</script>
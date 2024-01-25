<script>

import { ref } from 'vue'

export default {
  setup(props) {

    const show = ref(true);
    const list = ref([1, 2, 3]);
    return { list,  show }
  }
}
</script>

<template>
  <div>
    <div>
      <button @click=" show = !show ">toggle</button>    
      <button @click="list.push(list.length + 1)">Push Number</button>
      <button @click="list.pop(list.length - 1)">Push Number</button>
      <button @click="list.reverse()">Reverse List</button>
    </div>
    
    <div>
      <ul v-if="show && list.length">
        <li v-for=" i in list">
            {{ i }}
        </li>
      </ul>
      <p v-else-if="list.length">List is not empty, but hidden.</p>
      <p v-else>List is empty.</p>
    </div>
  </div>
</template>

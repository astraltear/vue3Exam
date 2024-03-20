<template>
  <div>
    <button v-on:click="toggle">토글 버튼</button>
    <p>{{ state.count }}</p>
    <h1 v-if="state.count">IN IF</h1>
    <h1 v-else="state.count">ELSE</h1>  
  </div>
  
</template>

<script>
/* eslint-disable no-unused-vars  */
import { reactive } from 'vue';

export default {
  setup () {
    const state = reactive({
      count: true,
    })

    function toggle() {
      console.log('toggle:', state.count)
      state.count = !state.count;

      // if(state.count){
      //   state.count = false;
      // } else {
      //   state.count = true;
      // }
    }
  
    return {
      state, toggle
    }
  }
}
</script>

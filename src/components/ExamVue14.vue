<script>

import { ref } from 'vue';

export default{
  
  setup(props) {
    
    const msg = ref('messages!!!!');

    function reverseMessage() {
      msg.value = msg.value.split('').reverse().join('')
    }

    function notify() {
      alert('navigation was prevented.')
    }

    return {  msg, reverseMessage, notify,   }
  }
}

</script>

<template>
<div>
  <!-- {{  }} 안에서 평가식을 쓸 수 있다  
    msg || 'other'   : msg가 비었으면 other를 출력한다.
    msg && 'other'   : msg가 있으면  other를 출력한다.
    -->
  <p>{{ msg || 'other' }}</p>

  <!-- Bind to a method/function.    The @click syntax is short for v-on:click.   -->
  <button @click="reverseMessage">Reverse Message</button>

  <!-- Can also be an inline expression statement -->
  <button @click="msg += '!'">Append "!"</button>

  <!--  Vue also provides modifiers for common tasks    such as e.preventDefault() and e.stopPropagation()  -->
  <a href="https://vuejs.org" @click.prevent="notify">  A link with e.preventDefault()  </a>

</div>
</template>
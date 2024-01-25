<script>

import { ref,computed } from 'vue';
import { marked } from 'marked';
import { debounce } from 'lodash-es';

export default{
  setup(props) {
    
    const input = ref('title');
    const output = computed(() => {
      console.log("computed!!!!!!!!!!!")
      return marked(input.value);
    })

    const update = debounce((e) => {
      console.log("debounce!!!!!!!!!!!")
      input.value = e.target.value
    }, 100)

    return { input, output,update, }
  }
}
</script>

<template>
  <div class="editor">
    <textarea  class="input" :value="input" @input="update"></textarea>
    <div class="output" v-html="output"></div>

  </div>
</template>


<style>
body {
  margin: 0;
}

.editor {
  height: 100vh;
  display: flex;
}

.input,.output {
  overflow: auto;
  width: 100%;
  height: 50%;
  box-sizing: border-box;
  padding: 0 20px;
}

.input {
  border: none;
  border-right: 1px solid #ccc;
  resize: none;
  outline: none;
  background-color: #f6f6f6;
  font-size: 14px;
  font-family: 'Monaco', courier, monospace;
  padding: 20px;
}

code {
  color: #f66;
}
</style>
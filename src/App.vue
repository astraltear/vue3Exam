<template>
  
<examvue1></examvue1>
<exam-vue2></exam-vue2>
<ExamVue3></ExamVue3>
  
</template>

<script>

import examvue1  from './components/ExamVue1.vue'
import ExamVue2 from './components/ExamVue2.vue';
import ExamVue3 from './components/ExamVue3.vue';

export default {
  components: {
    examvue1,
    ExamVue2,
    ExamVue3,

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

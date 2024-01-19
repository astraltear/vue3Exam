<!--
  v-bind: 단방향 데이터 바인딩을 위해 사용됩니다. 
          부모 컴포넌트의 데이터를 자식 컴포넌트로 전달하거나, 데이터를 동적으로 변경하고 싶을 때 사용됩니다
  v-model: 양방향 데이터 바인딩을 지원합니다. 
          주로 폼 요소와 함께 사용되어 부모 컴포넌트에서 자식 컴포넌트로 데이터를 전달하면서, 
          동시에 자식 컴포넌트에서 변경된 데이터를 부모 컴포넌트로 전달하는 경우에 사용됩니다
-->
<template>
  <div>
    <p>{{ message }}</p>
    <exam-vue9-child v-bind:prop-message="message" message2="PARAM2"></exam-vue9-child>
  </div>
</template>

<script>

import ExamVue9Child from './components/ExamVue9Child.vue'
export default {
  components:{
    ExamVue9Child,
  },

  setup() {
    const message = "Hello from parent";
    
    return {
      message,
    
    }
  }
}
</script>

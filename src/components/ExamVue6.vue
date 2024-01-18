<script>
/*
반응형이 되려면  ref가 필요하다.

ExamVue2를 제외한 1,3,4,5까지는 Options API를 사용한 경우이다.

Options API:
Options API는 Vue 2에서 사용되던 전통적인 API 스타일입니다. 
이는 컴포넌트 옵션을 객체로 정의하고, 데이터, 메서드, 라이프사이클 훅 등을 객체의 속성으로 선언하는 방식입니다. 
주로 간단한 컴포넌트나 작은 규모의 프로젝트에서 사용됩니다.


ExamVue2와 현재는 Composition API이다 
Composition API:
Composition API는 Vue 3에서 소개된 새로운 API 스타일로, 
코드를 더 모듈화하고 재사용 가능한 로직을 구성하기 위한 도구를 제공합니다. 
Composition API는 setup 함수 내에서 리액티브 상태와 로직을 정의하는 방식으로 사용됩니다.

Vue.js의 setup 함수에서 반환한 객체의 속성들을 직접 템플릿에서 참조하려면, 
해당 속성들을 템플릿에서 사용할 수 있도록 반응형 속성으로 정의해야 합니다

*/
import { ref, onMounted} from 'vue';

export default {
  setup() {
   const msg = ref('Im') ;
   let output=ref('');

   function showMsg() {
    //alert(msg.value);
    console.log(msg);
    output.value = msg.value; // ref(리액티브 특성)를 사용하면 이렇게 .value가 필요하다고 한다. 
                                // 변수가 아니라 객체의 특성을 띈다 
   }


   // watch 함수는 여러 개의 대상을 감시할 수도 있습니다. 예를 들어, 여러 개의 ref를 동시에 감시하려면 배열 형태
   // watch([message, count], ([newMsg, newCount], [oldMsg, oldCount]) => {
    watch(msg, () => {
      console.log('값이 변경되었습니다:',msg.value);
    });   

   onMounted(() => {
    console.log('component mounted')
   })

   const setupValue = ref({
      msg,
      showMsg,
      output,
    }); // ref로 감싸고 변수에 할당한다 

    return { setupValue }; // 변수를 객체로 변환해서 리턴한다 

  }
}

</script>

<template>
  <input v-model="setupValue.msg">
  
  <button @click="setupValue.showMsg">click</button>
  <p>{{ setupValue.output }}</p>
  <pre>{{ setupValue }}</pre>
</template>

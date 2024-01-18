<script setup>
/*
Composition API 이지만
script setup 이 있는 경우 ExamVue6과 비교하면 차이가 있다.

아래의 세 개의 과정이 필요가 없다. 
export default {
  setup() {
    return

*/
import { ref, onMounted, watch, reactive  } from 'vue';

/*
reactive()는 객체(배열, Map, Set과 같은 빌트인 타입 포함)에서만 작동
반면에 ref()는 모든 타입의 값을 사용할 수 있으며, 
.value 속성으로 내부 값을 노출하는 객체를 생성합니다.
*/
const counter = reactive({count: 0});
const msg = ref('');

function increment() {
  counter.count++;
}

onMounted(() => {
  console.log(`숫자 세기의 초기값은 ${ counter.count } 입니다.`)
});

// watch 함수는 여러 개의 대상을 감시할 수도 있습니다. 예를 들어, 여러 개의 ref를 동시에 감시하려면 배열 형태
// watch([message, count], ([newMsg, newCount], [oldMsg, oldCount]) => {
watch(msg, () => {
      console.log('값이 변경되었습니다:',msg.value);
});

</script>

<template>
  <button v-on:click="increment">{{ counter.count }}</button>
  <input v-model="msg">{{ msg.split('').reverse().join('') }} <!-- 유효한 JavaScript 표현식을 사용 가능   -->
</template>


<script setup>
/*
Composition API 이지만
script setup 이 있는 경우 ExamVue6과 비교하면 차이가 있다.

아래의 세 개의 과정이 필요가 없다. 
export default {
  setup() {
    return

*/
import { ref, onMounted, watch  } from 'vue';

const count = ref(0);
const msg = ref('');

function increment() {
  count.value++;
}

onMounted(() => {
  console.log(`숫자 세기의 초기값은 ${ count.value } 입니다.`)
});

// watch 함수는 여러 개의 대상을 감시할 수도 있습니다. 예를 들어, 여러 개의 ref를 동시에 감시하려면 배열 형태
// watch([message, count], ([newMsg, newCount], [oldMsg, oldCount]) => {
watch(msg, () => {
      console.log('값이 변경되었습니다:',msg.value);
});

</script>

<template>
  <button v-on:click="increment">{{ count }}</button>
  <input v-model="msg">{{ msg }}
</template>


<template>
  <div>
    <p ref="pElementRef">안녕</p>
    <button  @click="clickplus" >{{ count }}</button>
    <p v-if="!todoData">로딩...</p>
    <pre v-else>{{ todoData }}</pre>
  </div>
</template>

<script>
import { ref, onMounted, watch } from 'vue'
export default {
    setup(){
        const pElementRef = ref(null)
        const count = ref(0);
        
        onMounted( ()=> outerFun('parameter value!!!!') )

        function outerFun(param){
          // 템플릿 참조는 컴포넌트가 마운트된 후에만 접근할 수 있습니다.
          //pElementRef.value.textContent = '마운트 되었어요! ${param} ';
          pElementRef.value.textContent = `마운트 되었어요! ${param}`;
        }
        
        function clickplus(){
          count.value++;
        }

        /*
          watch 함수는 첫 번째 인자로 감시할 대상을 받고, 
          두 번째 인자로 감시 대상이 변경될 때 실행될 콜백 함수를 받습니다. 
          콜백 함수의 파람은 변경된 값과 이전 값에 대한 정보
        */
        // watch(count, (newCount) => {
        //   
        //   console.log(`새로 센 숫자 값은: ${newCount}`)
        // })

        watch(count, (newCount,oldCount) => watchFunc(newCount,oldCount)  )

        const todoData = ref(null);
        async function watchFunc(newCount,oldCount){
          console.log("call watchFunc:", newCount, oldCount);
          todoData.value = null;
          const res = await fetch(
            `https://jsonplaceholder.typicode.com/todos/${count.value}`
          )
          todoData.value = await res.json();
          console.log("todoData:::",todoData.value)

        }
        
      return { pElementRef, count,clickplus, todoData, }
    },
}

</script>
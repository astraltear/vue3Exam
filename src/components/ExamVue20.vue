<script>
/*

아래 URL의 설명을 자세히 
https://junglast.com/blog/vue3-props-reactive

vue는 재귀적으로 객체 내부의 모든 객체를 Proxy로 처리한다는 점



Vue 3에서는 ref와 reactive를 사용하여 상태를 관리 

ref는 기본적으로 단일 값을 가지는 반면, 
reactive는 객체를 관리 

toRefs는 Vue 3의 Composition API에서 사용되는 함수
이 함수는 reactive object를 기반으로 한 객체의 속성들을 
다시 참조로 변환해주는 역할

toRefs는 reactive로 생성된 객체를 사용할 때 특정 속성들을 참조로 변환해주는 역할
value속성을 사용하지 않아도 된다.( 속성과 값은 다르다  )

Vue 3에서 상태 관리를 위해 ref와 reactive를 사용할 때, 
객체 내의 속성에 접근할 때는 .value를 사용

ref는 기본적으로 단일 값을 갖는 반응적인 참조를 만들기 때문에 
.value를 사용하여 그 값을 가져와야 합니다. 
따라서 ref를 사용한 경우, 객체의 속성에 접근할 때에도 .value를 사용

toRefs는 reactive로 생성된 객체를 참조로 변환해주는데, 
이 때 .value를 사용하지 않아도 됩니다. 
toRefs를 사용하면 .value를 사용하지 않아도 원래 객체의 속성에 접근할 수 있게 됩니다.

toRefs 함수를 사용하지 않으면 객체의 각 속성이 참조가 아닌 원시 값으로 사용됩니다. 
즉, 일반적인 객체처럼 속성에 직접 접근하여 사용할 수 있습니다. 
그러나 Vue의 반응성 시스템을 이용하기 위해서는 .value를 사용해야 합니다.


*/

import { reactive, toRefs } from 'vue'

export default {
  setup () {
    const state = reactive({
      name: 'John',
      age: 30
    })
  
    function btn1(){
       const refsState = toRefs(state);
       console.log(refsState.name) // 참조로 변환된 속성, .value 없이 사용 가능
       console.log(refsState.name.value)  // 실제 값

       const newState = {...refsState}
       console.log(newState.name) // 참조로 변환된 속성, .value 없이 사용 가능
       console.log(newState.name.value)  // 실제 값
    }

   const refObject = ref({count: 0})
   const refPrimitive = ref(0);
   const reactiveState = reactive( {count : 0, contents: {title: "DEFAULT"} } )
   const plainState = {count : 0, contents: {title: "DEFAULT"} }

   console.log(refObject)
   console.log(refPrimitive)
   console.log(reactiveState)

   console.log(refObject.value.count)
   console.log(refPrimitive.value)
   console.log(reactiveState.count)

    return {
    //...toRefs(state),
    //  state,
    btn1,
    }
  }
}


</script>
<template>
  <div @click="btn1">1</div>
</template>
<template>
  <p>CHILD props propMessage: {{ propMessage }}</p>
  <p>CHILD props message2: {{ message2 }}</p>
<!--
    {{ msg || 'prop이 아직 전달되지 않았습니다!' }}는 Vue.js에서 사용되는 템플릿 문법 중 하나입니다. 
    이 문법은 데이터 바인딩과 함께 사용되어 msg라는 데이터가 존재하면 해당 값을 출력하고, 
    msg가 존재하지 않으면 대체 텍스트인 'prop이 아직 전달되지 않았습니다!'를 출력합니다.

    이것은 JavaScript의 논리 연산자 ||를 사용한 표현식입니다. 
    msg가 falsy한 값 (예: null, undefined, false, 0, '' 등)이면 대체값이 사용됩니다.

    예를 들어, msg가 Vue 컴포넌트의 props로 전달되는 경우에 해당합니다. 
    만약 msg가 전달되지 않았다면, 'prop이 아직 전달되지 않았습니다!'가 출력
-->
  <p>CHILD props message3: {{ message3  || 'prop이 아직 전달되지 않았습니다!'  }}</p>
</template>
<script>
export default{
  props: {
      propMessage: {type:String},
      message2 : String,
      message3 : String,
  }
}
</script>

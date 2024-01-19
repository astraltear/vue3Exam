
<script>

import { ref, watch } from 'vue'

export default {
  setup() {
    let titleClass = ref('');
    const picked = ref('');

    const plainVar ="";
    const refVar = ref("");
    console.log(plainVar)
    console.log(refVar)

    function setRed(){
      console.log("setRed")
      this.titleClass="title";
    }

    function setBlue(){
      console.log("setBlue")
      this.titleClass="title2"; // 리터럴 값으로 변수에 직접 값을 할당하는 경우 .value를 사용하지 않아도 정상적으로 동작

      /*
      원시 데이터 타입인 문자열에는 .value를 사용하지 않아도 됨
      titleClass.value = 'title2';

      참조형 데이터인 객체 또는 배열에는 .value를 사용해야 함
      titleClass.value = { color: 'blue' };
      titleClass.value = ['title2'];
      */
    }

    watch(picked,() => {
      console.log('picked::::',picked.value);
      titleClass.value = picked.value;  // ref로 감싸진 변수의 값을 변경할 때는 .value를 사용
    })

    /* 
      return에서 반응형 상태나 함수를 반환해야 한다고 한다.
      Option API를 보면 아래와 같이 객체를 담아서 data()함수를 반환한다.
      Option API의  data는 상태 데이터를 정의
        data(){return {} }
      
      data 옵션 안에서 정의된 데이터는 Vue.js에 의해 반응형으로 관리되며, 
      데이터가 변경될 때마다 관련된 뷰가 업데이트
    */
    return {titleClass,setRed,setBlue,picked };   // 갹체를 반환한다. 
  }
}

</script>

<template>
  <h1 v-bind:class="titleClass">CHANGE COLOR</h1>
  <div>
      <div>
        <input type="radio" value="title" v-model="picked">red
        <input type="radio" value="title2" v-model="picked">red
      </div>
      <div>
        <button @click="setRed">red</button>
        <button @click="setBlue">blue</button> 
      </div>
  </div>
</template>

<style>
.title {
  color: red;
}

.title2 {
  color: blue;
}
</style>
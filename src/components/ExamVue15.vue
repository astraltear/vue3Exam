<template>
  <div>
    <!-- tooltip 생성  -->
    <span :title="msg">AAAAAAAAAAAAA</span>
    
  </div>
  
  <!-- 
    v-bind:class 또는 간단히 :class 디렉티브를 사용하여 동적으로 클래스를 설정
    이 코드에서 red라는 클래스는 isRed라는 데이터 속성의 값에 따라 동적으로 적용
    만약 isRed가 true이면 해당 요소에 red 클래스가 적용되고, false이면 클래스가 제거됩니다.
   -->
  <p :class="{ red: isRed }" @click="toggleRed">
      This should be red... but click me to toggle it.
    </p>
  
    <p :style="{ color }" @click="toggleColor">
      This should be green, and should toggle between green and blue on click.
    </p>  
  </template>
  <script>
  
  import { ref } from 'vue';
  
  export default{
    setup(props) {
  
      const msg = ref('nothing');
      const isRed = ref(true)
      const color = ref('green');
  
      function toggleRed(){
        isRed.value = !isRed.value;
        console.log("isRed:", isRed.value );
      }
  
      function toggleColor() {
        color.value = color.value === 'green' ? 'blue' : 'green'
      }
  
      
      return { msg,isRed, color, toggleRed,toggleColor,  }
    }
  }
  </script>
  
  <style>
  .red {
    color: red;
  }
  </style>
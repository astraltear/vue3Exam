<!--
  <script>
      전통적인 Options API:
      Vue 2에서 사용되던 Options API 방식입니다.
      data, computed, methods, watch, created 등의 옵션을 사용하여 컴포넌트를 정의합니다.
      명시적인 선언과 데이터 관리가 가능하지만 코드가 길어질 수 있습니다.

  <script setup>
      Composition API 사용을 위한 단축 구문:
      Vue 3에서 소개된 Composition API와 함께 사용하는 단축 구문입니다.
      defineProps, defineEmits, ref, reactive, watch 등의 Composition API를 간결하게 사용할 수 있습니다.
      Props, Emits, Reactive state 등이 더 간결하게 정의됩니다.

  차이점 요약
      <script>은 Options API를 사용하고, <script setup>은 Composition API를 사용합니다.
      <script setup>은 더 간결하게 코드를 작성할 수 있어 가독성이 높아집니다.
      <script setup>은 자동으로 defineProps와 defineEmits를 포함하므로 명시적으로 선언하지 않아도 됩니다.
      <script setup>은 선언적인 형태로 Props를 정의할 수 있어 가독성이 향상됩니다.

  <script>
      export default {
        data() {
          return {
            message: 'Hello from script block!',
          };
        },
        methods: {
          updateMessage() {
            this.message = 'Updated message!';
          },
        },
      };
  </script>


  <script setup>
    import { ref } from 'vue';

    const message = ref('Hello from script setup block!');

    function updateMessage() {
      message.value = 'Updated message!';
    }
  </script>


  1. data
      Options API에서 사용:
      Vue 2에서 사용되는 Options API에서 주로 활용됩니다.
      컴포넌트 내부에서 data 함수를 정의하고 그 안에 데이터를 반환하는 형태로 사용합니다.
      data 함수에서 반환된 객체의 프로퍼티들은 컴포넌트 인스턴스의 데이터로 사용됩니다.
      Vue 인스턴스에 등록된 데이터로, 컴포넌트 내에서 this.$data로 접근 가능합니다.  

      <script>
        export default {
          data() {
            return {
              message: 'Hello from data!',
            };
          },
        };
      </script>

  
  2. ref
      Composition API에서 주로 사용:
      Vue 3에서 도입된 Composition API에서 주로 활용됩니다.
      ref 함수를 사용하여 데이터를 감싸는 형태로 사용합니다.
      ref로 감싼 변수에 접근할 때는 .value를 사용해야 합니다.
      주로 로컬 변수를 선언하고 사용하는 용도로 활용됩니다.

      <script>
          import { ref } from 'vue';

          export default {
            setup() {
              const message = ref('Hello from ref!');
              return { message };
            },
          };
      </script>

  주요 차이점
      API 사용 위치:
          data는 Options API에서 사용되며, ref는 Composition API에서 주로 사용됩니다.
      선언 방식:
          data는 함수 안에서 객체를 반환하는 형태로 선언됩니다.
          ref는 함수를 호출하고 반환된 객체를 변수에 할당하는 형태로 선언됩니다.
      데이터 접근 방식:
          data로 선언된 데이터에는 this.$data.property 형태로 접근합니다.
          ref로 선언된 변수에는 .value를 사용하여 접근합니다.
      Composition API에서의 활용:
          Vue 3에서는 Composition API를 사용할 때 주로 ref를 활용하여 로컬 상태를 정의합니다.
      
-->

<template>
  <div>
    {{ count }}<button v-on:click="increase">click</button><hr>
    <input v-bind:value="txt1" v-on:input="onInput" >{{ txt1 }}<hr>
    <input v-model="txt2">{{ txt2 }}
  </div>
</template>

<script>
import { ref,reactive } from 'vue';

export default {

  data () {
    return {  txt1: "", txt2: "", count : 0,    }
  },
  methods: {
    onInput(e){
      this.txt1 = e.target.value;
    },
    increase(){
      this.count++;
    }
  },

/*
  setup(props) {
    let count = ref(0);
    
    const txt1 = ref('');
    const txt2 = ref('') ;

    function increase(){
      this.count++;
    }

    function onInput(e){
      txt1.value = e.target.value;
    }

    return {  count,  increase, txt1, onInput,  txt2,  }
  },
*/  

/*
setup() {
  const dataObj = reactive({
    count : 0,
    txt1  : "",
    txt2  : "",
  });

  function increase(){
      this.count++;
    }

  function onInput(e){
    txt1.value = e.target.value;
  }

  return { dataObj,increase,onInput }
  // template 에서 사용할 때는   dataObj.count , dataObj.txt1, dataObj.txt2
}
*/


}
</script>

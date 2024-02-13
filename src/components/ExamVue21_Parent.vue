<template>
  <!-- String과 다른 데이터 유형을 가진 props를 전달하려면 전달하려는 속성 앞에 v-bind:를 작성해야 합니다. -->
  <ExamVue21_Child food-name="Apple" message="I like apples" v-bind:is-favorite="true"></ExamVue21_Child>  
  <ExamVue21_Child foodName="Banana" message="I like bananas"  v-bind:is-favorite="false"></ExamVue21_Child>  
  <ExamVue21_Child food-name="Pizza"/>
  <ExamVue21_Child food-name="Rice"/>
</template>

<script>
import ExamVue21_Child from './components/ExamVue21_Child.vue';

export default{
    setup(props) {
        return {  };
    },
    components: { ExamVue21_Child }
}
</script>

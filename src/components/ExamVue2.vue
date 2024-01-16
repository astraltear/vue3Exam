<template>
 <h1>Vue2</h1>
refmsg : <input type="text" id="inputText" v-model="refmsg"><br>
{{ refmsg }}<br>

단반향 바인딩 : <input type="text" v-bind:value="abbr"><br>
{{ abbr }}<br>
<hr>

<button @click="upvote">votes {{ votes }}</button><br>
<p v-if="votes < 5">counter less 5</p>
<p v-else-if="votes === 5">counter is 5</p>
<p v-else>votes bigger 5</p>
<hr>

<ol>
<!--
<div v-for="(item, index) in items"></div>  array
<div v-for="(value, key) in object"></div>  object 
<div v-for="(value, name, index) in object"></div> object    
-->    
    <li v-for="(value, key, idx) in objItem" v-bind:key="idx">
        idx: {{idx}},key:{{key}},elem:{{value}}
    </li>
</ol>
objItem : {{ objItem }}
<hr>


<input type="text" v-model="result.name">
<input type="radio" name="gender" v-model="result.gender" value="male">M
<input type="radio" name="gender" v-model="result.gender" value="female">W   
<hr>


<span v-for="hobby in hobbys" v-bind:key="hobby">
<input type="checkbox" v-model="result.hobby" v-bind:value="hobby">
<label>{{hobby}}</label>
</span>
<hr>



<select v-model="result.country">
<option v-for="(element, index) in countrys" v-bind:key="index">
{{index}}.{{element}}
</option>
</select>
<hr>
=========================$ExamVue2 data start===========================
<div>result : {{ result }}</div>
=========================$ExamVue2 data end===========================
<hr>
</template>

<script >
import {reactive, ref,onBeforeMount,onMounted,onBeforeUpdate,onUpdated,onBeforeUnmount,onUnmounted } from 'vue'

export default {
/*
 
  setup 함수는 Vue 3에서 도입된 새로운 옵셔널 API 중 하나입니다. 
  이 함수는 컴포넌트의 초기 설정을 담당하며, 
  data, computed, methods, watch, props 등과 같은 옵션 API를 대체

*/
  setup(){
    
    onBeforeMount(() => {
      console.log('컴포넌트가 마운트되기 전에 실행됨');
    });

    
    onMounted(() => {
      console.log('컴포넌트가 마운트된 후에 실행됨');
    });

    
    onBeforeUpdate(() => {
      console.log('컴포넌트가 업데이트되기 전에 실행됨');
    });

    
    onUpdated(() => {
      console.log('컴포넌트가 업데이트된 후에 실행됨');
    });

    
    onBeforeUnmount(() => {
      console.log('컴포넌트가 언마운트되기 전에 실행됨');
    });

    
    onUnmounted(() => {
      console.log('컴포넌트가 언마운트된 후에 실행됨');
    });

/*
    const는 상수를 선언할 때 사용되며, 한 번 할당된 값을 변경할 수 없습니다.
    let은 변수를 선언할 때 사용되며, 값을 재할당할 수 있습니다.

    이러한 Composition API 함수들은 Vue 3에서 도입되었으며, 
    구성 기반 API로 코드를 조직화하고 재사용 가능한 로직을 생성하는 데 유용
    ref()와 reactive()는 Vue의 반응성 시스템을 활용하여 데이터를 관리하고 화면을 업데이트하는 데 도움

*/
// ref로 원시값을 반응형으로 만들기
    const refmsg = ref('');  
    const abbr = ref('sample');
    let votes=ref('0');

    const objItem = {"one":'first', "two":'second', "three":'third', "four":'fourth' }

    const name ='';
    const gender='';
    const hobby=[];
    const hobbys = ['sports','photo','music','movie']
    const country ='';
    const countrys = ['kr','us','cn','jp']

    const result = reactive( {name, gender,hobby,country} )

    return { refmsg, abbr,votes   ,objItem,   result  ,hobbys,countrys  }

    
  },
  methods: {
    upvote: function(evt){
        if(evt){  evt.preventDefault() }
        this.votes++;
    }
  },

  

  
}
</script>
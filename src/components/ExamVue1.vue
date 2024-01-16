<template>
 <h1>Vue1</h1>
<!--  
  v-model , v-bind

      v-model은 주로 폼 입력 요소와 함께 사용되며, 양방향 데이터 바인딩을 처리합니다.
      v-bind는 엘리먼트의 속성을 동적으로 설정하기 위해 사용되며, 단방향 데이터 바인딩을 처리합니다.
      v-model은 주로 입력 요소와 함께 사용되어 사용자 입력과 데이터를 양방향으로 동기화합니다.
      v-bind는 HTML 속성에 Vue 데이터 값을 동적으로 설정할 때 사용됩니다. 

  @, :
      @는 이벤트 바인딩에 사용되는 단축어로, 이벤트 리스너를 설정할 때 주로 사용됩니다.
      :는 v-bind의 단축어로, 엘리먼트의 속성을 동적으로 설정할 때 사용됩니다.
      둘 다 Vue의 템플릿에서 코드를 간결하게 작성하기 위한 단축어입니다.
      주로 @는 이벤트 처리에, :는 데이터 바인딩에 사용됩니다. 
-->



<input type="radio" id="option1" value="option1" v-model="selectedOption" >Option 1
<input type="radio" id="option1" value="option2" v-model="selectedOption" >Option 2
<input type="radio" id="option1" value="option3" v-model="selectedOption" >Option 3<br>
selectedOption : {{ selectedOption }}<br>
<hr>

msg : <input type="text" id="inputText" v-model="msg"><br>
msg : {{ msg }}<br>
<hr>

gender: <input v-model="gender"><br>
<div v-if="gender==='F'">MISS {{msg}}</div>
<div v-if="gender==='M'">MR {{msg}}</div>
<hr>

stories : {{ stories }}<br>
<li v-for = " s in stories" v-bind:key="s.plot">
    {{s.plot}}  ||  {{s.writer}} 
</li>
<hr>


<li v-for = " i in 3" v-bind:key="i">
    {{ i }} times {{ i * 4 }}
</li>
<hr>


<button @click="upvote">votes {{ votes }}</button>
<hr>

=========================$ExamVue1 data start ===========================
<div>data : {{ $data }}</div>
=========================$ExamVue1 data end ===========================
<hr>

</template>

<script>

export default {
/*
    data 속성은 컴포넌트의 상태 데이터를 정의하는 데 사용되는 옵션
    data는 함수로 정의되며, 이 함수는 컴포넌트의 각 인스턴스에 대해 호출되어 해당 인스턴스에 속한 데이터 객체를 반환

    아래와 같이 객체로 작성할 수도 있으나 
    여러 인스턴스에서 데이터를 공유하게 되므로 원하지 않는 동작이 발생할 수 있습니다.
    data: {
      message: '안녕하세요, Vue!'
    }
*/
  data(){
    return {
      selectedOption : 'option3',
      msg: '',
      gender:'',
      votes : 0,
      stories :  [
            {plot:"i crash", writer : "alex"},
            {plot:"yes", writer :"john"},
            {plot:"yes", writer :"smith"}
        ],
    }
  },
  methods: {
    upvote : function(evt){
      console.log(evt);
      this.votes++;
    }
  },
}
</script>

<!--

<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>

    var str_array =  [
        {plot:"i crash", writer : "alex"},
        {plot:"yes", writer :"john"},
        {plot:"yes", writer :"smith"}
    ]; 

    var data = { 
        msg : "greeting vue!!!!",
        gender :"",
        name : "",
        stories : str_array,
        votes : 0
        };

    new Vue({
        el:'#app',
        data: data,

        methods: {
            upvote : function () {
                this.votes++;
            }
        },
    })
</script>
  
-->
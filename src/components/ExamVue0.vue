<template>
<!--

화살표 함수 설명
this 바인딩: 화살표 함수는 자신만의 this를 생성하지 않고, 
            주변 범위의 this를 그대로 사용합니다. 
            따라서 일반 함수와는 달리 this가 함수 내부에서 변경되지 않습니다.

인자가 하나인 경우 괄호 생략 가능

단일 표현식인 경우 중괄호 및 return 생략 가능: 
            함수가 단일 표현식으로 구성되어 있는 경우 중괄호 및 return을 생략
            이 경우 표현식의 결과가 자동으로 반환

function add(a, b) {                        const add = (a, b) => {
  return a + b;                 ==>              return a + b;
}                                           }


// 매개변수가 하나인 경우
const square = x => x * x;

// 매개변수가 두 개인 경우
const add = (a, b) => a + b;

// 복수의 표현식이 있는 경우
const multiply = (a, b) => {
  const result = a * b;
  return result;
};


v-text
v-html
v-model
v-on:click  @click    
-->

 <h1>Vue0</h1>
 <p>{{ mytext }}</p>
 <p v-text="mytext"></p>
 <p v-html="myhtml"></p>
 <p v-text="myArray[0]"></p>
 <p v-text="myTea[1].name"></p>
 <p><input v-model="myName">나는 {{ myName }} 입니다.</p>
 <p><input type="checkbox" v-model="myCheck"> 체크박스의 상태는 {{ myCheck }} </p>
 <P>
    <input type="radio" value="red"   v-model="picked"> 적
    <input type="radio" value="green" v-model="picked"> 녹
    <input type="radio" value="blue"  v-model="picked"> 청<br>
    {{ picked }}이 선택됨
 </P>
 <p><button v-on:click="countUp">{{ count }}</button> </p>
 <p> <input v-model="price" type="number">{{ taxIncluded }} </p>

<hr> 


=========================ExamVue0 data start===========================
<div>data : {{ $data }}</div>
=========================ExamVue0 data end===========================
<hr>


</template>
<script>

let teaList = [
    {name   :'다즐링', price:600},
    {name   :'얼그레이',price:500},
    {name   :'실론',price:500}
    ]

export default {
    data() {
        return {
            mytext: "here",
            myhtml: "<div>html code</div>",
            myArray : ['다즐링','얼그레이','실론'],
            myTea : teaList,
            myName:"",
            myCheck: true,
            picked: "red",
            count: 0,
            price : 0,
        }
    },
    methods: {
        countUp: function(){
            this.count++;
        }
    },
    computed:{
        taxIncluded : function () {
            return this.price * 1.1;
        }
    },
    watch:{
        count : function(){
            console.log("watch count value:"+this.count);
        }
    }
}
</script>
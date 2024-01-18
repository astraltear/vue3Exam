<template>
<!--
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
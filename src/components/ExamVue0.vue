<template>
 <h1>Vue0</h1>
 <p>{{ mytext }}</p>
 <p v-text="mytext"></p>
 <p v-html="myhtml"></p>
 <p v-text="myArray[0]"></p>
 <p v-text="myTea[1].name"></p>
 <input v-model="myName">
 <p>나는 {{ myName }} 입니다.</p>
<hr> 


=========================ExamVue0 data start===========================
<div>data : {{ $data }}</div>
=========================ExamVue0 data end===========================
<hr>


</template>
<script>

let teaList = [
    	{name:'다즐링', price:600},
        {name:'얼그레이',price:500},
        {name:'실론',price:500}
    ]

export default {
    data() {
        return {
            mytext: "here",
            myhtml: "<div>html code</div>",
            myArray : ['다즐링','얼그레이','실론'],
            myTea : teaList,
            myName:"",
        }
    }
}
</script>
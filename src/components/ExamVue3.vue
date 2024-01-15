<template>

<ul>
    <li v-for="i in fruits" v-bind:key="i">{{i}} </li>
</ul>
<hr> 

<button @click="sayHello">confirm</button>
<hr>

<p> 원본 메시지: <input type="text" id="msg1" v-model="message"></p>
<p>대문자로 변환: {{ upperCaseMessage }}</p>
<hr>


<input type="number" name="price" v-model="price">
<div>reservedTitle: {{reservedTitle}}</div>
<div>supplyAmt: {{supplyAmt}}</div>

</template>
<script>
/* eslint-disable */
export default {
    data() {
        return {
            fruits : [1,2,3,4,5],
            price : 100,
            message : 'vue is the app best package!'
        }
    },
    methods : {
        sayHello : function(){
            alert(this.fruits)
        }
    },
    /*
    computed 속성을 사용하면 템플릿에서 계산된 값에 접근할 수 있으며, 해당 값이 변경될 때만 다시 계산
    */
    computed:{
        supplyAmt: function(){
            return (this.price/11) * 10 ;
        },
        upperCaseMessage: function(){
            return this.message.toUpperCase();
        },
        reservedTitle : function () {
                console.log("reservedTitle");
                let temp = this.price;
                return "computed actived"+Math.random();
            },

    }
}
</script>
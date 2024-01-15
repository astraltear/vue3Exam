<template>
 <h1>Vue3</h1>
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
<div><input type="text" name="inverse" v-model="inversetxt"></div>
<div><input type="text" name="reverse" v-model="reversetxt"></div>
<hr>

</template>
<script>
/* eslint-disable no-unused-vars  */
/* eslint-disable vue/no-deprecated-destroyed-lifecycle */
export default {
    data() {
        return {
            fruits : [1,2,3,4,5],
            price : 100,
            message : 'vue is the app best package!',
            inversetxt :'',
            reversetxt : '',
        }
    },
    methods : {
        sayHello : function(){
            alert(this.fruits)
        }
    },
    /*

    computed 프로퍼티는 data 객체 내 프로퍼티에 변화가 발생할 때마다 반응하도록 설정

    reservedTitle function에서 
    let temp = this.price; 이 부분이 없으면 해당 함수는 계속 호출되지 않는다. 
    변화를 감지할 프로퍼티를 선언(?) 하지 않아서 작동을 안 하는 것 같음
    supplyAmt에도 this.price가 있으므로 
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
    },
    /*
        watch 프로퍼티는 data 객체 내의 데이터를 모니터링할 수 있으며, 
        특정 데이터에 변화가 발생하면 후속 처리를 한다.
    */
    watch : {
        inversetxt : function(val){
            this.inversetxt = val;
            this.reversetxt = val.split('').reverse().join('');
        },
        reversetxt : function(val){
            this.reversetxt = val;
            this.inversetxt = val.split('').reverse().join('');
        }
    },
    beforeCreate() { console.log('beforeCreate')  },
    created() { console.log('created')  },
    beforeMount() {   console.log('beforeMount') },
    mounted() {  console.log('mounted') },
    beforeUpdate()  {  console.log('beforeUpdate') },
    updated() { console.log('updated')  },
    destroyed() {  console.log('destroyed')  },
}
</script>
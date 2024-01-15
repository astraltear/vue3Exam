<template>
 <h1>Vue4</h1>
<li v-for=" e in elects" v-bind:key="e.name">
    {{e.name}}  ||  {{e.count}} <button v-on:click="e.count++">votes</button>
</li>

<hr> 
=========================$ExamVue4 data start===========================
<div>data : {{ $data }}</div>
=========================$ExamVue4 data end===========================
<hr>
</template>
<script>

export default {
    data() {
        return {
            elects : [
                {name:"black", count : 0},
                {name:"pink", count :0},
                {name:"white", count :0},
                {name:"brown", count :0} 
            ]        
        }
    },
}
</script>
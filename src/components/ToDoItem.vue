<template>
 <h1>ToDoItem</h1>
 <div>
    <input type="checkbox" 
        :id="id"
        :checked="isDone"
    />{{ label }}
 </div>

=========================$ToDoItem data start===========================
<div>data : {{ $data }}</div>
<div>props : {{ $props }}</div>
=========================$ToDoItem data end=========================== 
</template>
<script>
export default{
    props : {
        id: { required: true, type: String },
        label : {require:true, type:String},
        done : {default:false, type:Boolean},
    },
    data() {
        return {  isDone: this.done, }
    },

}
</script>
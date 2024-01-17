<template>
 <div>
    <input type="checkbox" 
        :id="id"
        :checked="isDone"
        @change="changeCheckUpdate(id)"
    />{{ label }}
 </div>

=========================ToDoItem data start===========================
<div>data : {{ $data }}</div>
<div>props : {{ $props }}</div>
=========================ToDoItem data end=========================== 
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
    methods: {
        changeCheckUpdate: function (id){
            console.log("changeCheckUpdate::"+id);
            this.$emit('checkbox-changed',{uid:id});
        }
    },

}
</script>
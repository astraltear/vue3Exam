<template>
 <div>
    <input type="checkbox" 
        :id="id"
        :checked="isDone"
        @change="changeCheckUpdate(id)"
    />{{ label }}
    <div>
    <div v-if="isEditing">
        <to-do-item-edit-form
        v-bind:id="id"
        v-bind:label="label"
        @item-edited="itemEdited"
        @edit-cancelled="editCancelled"
        ></to-do-item-edit-form>
    </div>
    
        <button type="button" @click="toggleToItemEditForm">Edit</button>
        <button type="button" @click="deleteToDo">Delete</button>

    </div>
 </div>

=========================ToDoItem data start===========================
<div>data : {{ $data }}</div>
<div>props : {{ $props }}</div>
=========================ToDoItem data end=========================== 
</template>
<script>
import ToDoItemEditForm from '../components/ToDoItemEditForm.vue';


export default{
    components:{
        ToDoItemEditForm,
    },
    props : {
        id: { required: true, type: String },
        label : {require:true, type:String},
        done : {default:false, type:Boolean},
    },
    data() {
        return {  
            isDone: this.done, 
            isEditing : false,
        }
    },
    methods: {
        changeCheckUpdate: function (id){
            console.log("changeCheckUpdate::"+id);
            this.$emit('checkbox-changed',{uid:id});
        },
        toggleToItemEditForm(){
            this.isEditing = true;
        },
        editCancelled() {
            this.isEditing = false;
        },
        itemEdited(newLabel) {
            console.log("ToDoItem itemEdited newLabel::"+newLabel);
            this.$emit('item-edited2', newLabel);
            this.isEditing = false;
        },
        deleteToDo() {
            this.$emit('item-deleted');
        },

    },
    

}
</script>
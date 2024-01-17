<template>
    <form>
        <label for="new-todo-input"> What needs to be done? </label>
        <input
        type="text"
        id="new-todo-input"
        name="new-todo"
        autocomplete="off" 
        v-model.lazy.trim="label"/>
        <button type="submit" v-on:click="onSubmit">Add</button>
    </form>
 

=========================ToDoForm data start===========================
<div>data : {{ $data }}</div>
<div>props : {{ $props }}</div>
=========================ToDoForm data end=========================== 
</template>
<script>
export default{
    methods : {
        onSubmit: function (evt) {
            if(evt){ 
                evt.stopPropagation();
                evt.preventDefault(); 
            }

            if(this.label===''){
                return;
            }

            console.log("form submitted", this.label);
            this.$emit("todo-added",this.label);
            this.label='';
        }
    },
    data() {
        return {
            label: "",
        };
    },
}
</script>
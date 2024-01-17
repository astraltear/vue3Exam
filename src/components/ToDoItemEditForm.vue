<template>
   <form  @submit.prevent="onSubmit">
    <div>
      <label>Edit Name for {{label}}</label>
      <input
        :id="id"
        type="text"
        autocomplete="off"
        v-model.lazy.trim="newLabel" />
        
        <div>
            <button type="button"  @click="onCancel">Cancel</button>
            <button type="submit" >Save</button>
        </div>
        <hr>
    </div>
   </form> 
</template>
<script>
  export default {
    props: {
        label: { type: String, required: true, },
        id: {  type: String, required: true,},
    },
    data() {
      return {
        newLabel: this.label,
      };
    },
    methods: {
      onSubmit() {
        
        if (this.newLabel && this.newLabel !== this.label) {
            console.log("ToDoItemEditForm onSubmit: IN IF",this.label,this.newLabel)
            this.$emit("item-edited", this.newLabel);
        }
      },
      onCancel() {
        this.$emit("edit-cancelled");
      },
    },
  }
</script>

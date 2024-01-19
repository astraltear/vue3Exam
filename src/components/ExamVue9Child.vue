<template>
  <p>CHILD props propMessage: {{ propMessage }}</p>
  <p>CHILD props message2: {{ message2 }}</p>
</template>
<script>
export default{
  props: {
      propMessage: {type:String},
      message2 : String,
  }
}
</script>

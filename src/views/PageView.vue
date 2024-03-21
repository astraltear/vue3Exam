<template>
  <h1>This is an PAGE</h1>
</template>
<script setup>
/* eslint-disable no-unused-vars  */

import {useRoute} from 'vue-router'


const route = useRoute();

// http://localhost:8080/page/tagname?is=eeeee&abc=444444&param1=aaaa
const id = route.params;
console.log("id=====>",id ); // { "id": "tagname" }

const paramValue = route.query;

// {"is": "eeeee", "abc": "444444",  "param1": "aaaa" }
console.log("paramValue=====>",paramValue); 


</script>
<template>

<input v-model="name" >
<button @click="searchAct">search</button>
<div>
<li v-for="it in result.searchResults" :key="it.id">
  {{ it.title }}
</li>
</div>

</template>

<script setup>
import { ref, computed, watch, reactive } from 'vue'
/* eslint-disable */

const name=ref('');
let result= reactive({searchResults : []})

const searchAct = function () {
  result.searchResults=[];
  console.log(name.value)
  result.searchResults=fetchSearchResults(name.value);
  console.log(result.searchResults)
}

const fetchSearchResults= (searchText) => {

  let stories = [
        { id: 1, title: "a" },
        { id: 2, title: "b" },
        { id: 3, title: "c" },
        { id: 4, title: "d" },
        { id: 5, title: "e" }
      ]

  return stories.filter(
      function(it){
          return it.title === searchText;
      }
  )

}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

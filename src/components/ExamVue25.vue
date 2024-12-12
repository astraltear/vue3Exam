<template>

<input v-model="name" >
<button @click="searchAct">search</button>
<div v-for="it in result.searchResults" :key="it.id">
  {{ it.title }}
</div>

</template>

<script setup>
import { ref, computed, watch, reactive, onMounted, onBeforeMount } from 'vue'
import axios from 'axios'
/* eslint-disable */

const name=ref('');
let result= reactive({searchResults:[]})
 

// let stories = [];


onMounted( async function(){
  console.log('컴포넌트가 마운트된 후에 실행됨');
  // stories.push({ id: 1, title: "a" });
  // stories.push({ id: 2, title: "b" });
  // stories.push({ id: 3, title: "c" });
  // stories.push({ id: 4, title: "d" });
  // stories.push({ id: 5, title: "e" });

  try {
     const response  = await axios.get('https://jsonplaceholder.typicode.com/posts/')
     result.searchResults = response.data
     //  console.log(response.data)
    //  console.log(result.searchResults)
    
  } catch (error) {
    console.log(error)
  }
} );

const searchAct = async function () {
  result.searchResults=[];
  console.log(name.value)
  result.searchResults.push(await fetchSearchResults(name.value)) ;
  console.log("here::",result.searchResults)
}

const fetchSearchResults= async (searchText) => {
  try {
    const response  = await axios.get('https://jsonplaceholder.typicode.com/posts/'+searchText);
    return response.data;
  } catch (error) {
    console.error('데이터 fetching 오류:', error);
    return []; // 오류 발생 시 빈 배열 반환
  }
  // return stories.filter(
  //     function(it){
  //         return it.title === searchText;
  //     }
  // )

}
/*

onBeforeMount(() => {
      console.log('컴포넌트가 마운트되기 전에 실행됨');
    });



<============================================
// watch
const filterTxt=ref('');
watch(filterTxt, (val) => {
  search.value= obj1.stories.filter(
      function(story){
          return story.writer === val;
      }
  )
});

// computed
const search=ref('');
 const search=computed( () =>{
   return obj1.stories.filter(
       function(story){
           return story.writer === filterTxt.value;
       }
   )
 })


// methods 
let search2=ref("");
const filterStory = () =>{
  search2.value = obj1.stories.filter(
      function(it){
          return it.plot.includes(filterTxt.value) ;
      }
  )
}
======================================>
*/
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

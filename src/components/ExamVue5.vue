<template>
 <h1>Vue5</h1>
<li v-for=" s in filterStory('alex')" v-bind:key="s.plot">
    s: {{s.plot}}
    <input v-model="s.vote">
</li>

<hr> 
<h1>famous.length : {{famous.length }}  </h1>
<p>famous:{{ famous }}</p>
<hr> 

<input v-model="query">
<h1>search.length : {{search.length }}</h1>
<p>search:{{ search }}</p>


=========================$ExamVue5 data start===========================
<div>data : {{ $data }}</div>
=========================$ExamVue5 data end===========================
<hr>


</template>
<script>

export default {
    data() {
        return {
            stories :[
                    {plot:"i car", writer : "alex", vote:34},
                    {plot:"yesterday", writer :"john", vote:54},
                    {plot:"are my", writer :"john", vote:4},
                    {plot:"at some", writer :"alex", vote:84}
                ],  
                query:'',   
        }
    },
    methods : {
        filterStory : function(filterWriter){
            console.log("filterStory")
            return this.stories.filter(
                function(story){
                    return story.writer === filterWriter;
                }
            )
        }
    },
    computed : {
        famous : function () {
            console.log("famous")
            return this.stories.filter(
                function(it){
                    return it.vote > 4;
                }
            )
        },
        search : function () {
            console.log("search")
            var query = this.query;
            return this.stories.filter(
                function (it) {
                    return it.plot.includes(query);
                }
            )
        }
    }
}
</script>
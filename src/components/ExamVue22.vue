<template>
  <div>
    <greeting></greeting>
    <div>
      <buttonCounter/>
      <buttonCounter></buttonCounter>
    </div>
    <div>
      <blog-post v-for=" post in posts"
      v-bind:title="post.title"></blog-post>
    </div>
  </div>

</template>

<script>

import { ref , onMounted } from 'vue'

export default {
  
    setup() {
      const posts = ref({});

      onMounted( async () =>{
        try {
          const response = await fetch('https://jsonplaceholder.typicode.com/posts')
          const jsondata = await response.json();
          posts.value = jsondata;
        } catch(e){
          console.error('Error fetching data:', e);
        }
      });

      // fetch('https://jsonplaceholder.typicode.com/posts')
      // .then(function (response) {
      //   return response.json()
      // })
      // .then(function (data) {
      //   console.log(data);
      //   posts = data
      // })

      return {posts, }
    },
  
    components : {
      Greeting : {
        template : '<h1>Welcome to components!</h1>'
      },
      buttonCounter : {
          setup() {
            const count =ref(0) ;
            return {count, }
          },
          /*
          setup  or data로 사용할 수 있음 
          data() {
            return  {count : 0 }
          },
          */
          template: '<button v-on:click="count++">You clicked me {{ count }} times.</button>'
      },
      blogPost : {
        props : {title : String },
        template: '<h3>{{ title }}</h3>'
      },

    }
}
</script>

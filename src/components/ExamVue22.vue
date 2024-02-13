<template>
  <div>
    <greeting></greeting>
    <alert-box>Something bad happened.</alert-box>
    <div>
      <buttonCounter/>
      <buttonCounter></buttonCounter>
    </div>
    <div :style="{ fontSize: postFontSize + 'em' }">
      <blog-post v-for=" post in posts"
      v-bind:post="post"
      v-on:enlarge-text="postFontSize += 0.1"></blog-post>
    </div>
  </div>

</template>

<script>

import { ref , onMounted } from 'vue'

export default {
  
    setup() {
      const posts = ref({});
      const postFontSize=ref(1) ;

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

      return {posts, postFontSize, }
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
        props : {post : Object },
        template: `<h2>{{post.userId}} :{{post.id}}</h2>
                  <h3>{{ post.title }}</h3>
                  <h4>{{post.body}}</h4>
                  <button v-on:click="$emit('enlarge-text')">Enlarge text</button>
                `
        
      },
      alertBox : {
        template: `<div class="demo-alert-box">
                      <strong>Error!</strong>  
                      [<slot></slot>]   
                  </div>`
      },

    }
}
</script>

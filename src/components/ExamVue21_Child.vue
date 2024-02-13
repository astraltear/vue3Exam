<template>
  <ul>
      <li v-on:click="countClicks">
          <h2>{{ foodName }}</h2>
          <p>{{ message }}</p>
          <p v-show="isFavorite">{{ isFavorite }}</p>
          <p id="red">You have clicked me {{ clicks }} times.</p>
      </li>
  </ul>
</template>

<script>
import { ref } from 'vue'
export default{

  props :{
      foodName : String,
      message : {type : String , required : true, default :  'This is the default description.' } ,
      isFavorite : Boolean,
  },

/*   
  위와 같이 객체 혹은 아래와 같이 배열로 선언할 수 있다.
  
 props: ["foodName", "message",'isFavorite'],
*/
  setup(props) {

      //const foodName ="Apples";
      //const message='I like apples'
      const clicks= ref(0)

      //return {foodName,message, clicks, countClicks }    
      return { clicks, }    
  },

  methods: {
      countClicks :  function (){
          console.log(this.foodName, "countClicks")
          this.clicks++;
      }
  },
}
</script>

<style>

#red {
font-weight: bold ;
color: rgb(144, 12, 12);
}
</style>
<template>
  <div>
    <div>
      <button
      v-for="tab in tabs"
      v-bind:key="tab"
      v-bind:class="['tab-button', { active: currentTab === tab }]"
      v-on:click="currentTab = tab"
      >{{ tab }}</button>
    </div>

    <!-- 
    v-bind:is는 Vue.js에서 동적 컴포넌트를 처리하기 위한 디렉티브입니다. 
    이 디렉티브를 사용하면 런타임 중에 어떤 컴포넌트를 렌더링할지 동적으로 결정할 수 있습니다.
    일반적으로 Vue.js에서 컴포넌트를 렌더링할 때는 정적인 방법으로 컴포넌트를 선언하고 사용합니다. 
    그러나 때로는 런타임 중에 어떤 컴포넌트를 사용할지 결정해야 하는 경우가 있습니다. 
    이때 v-bind:is 디렉티브가 유용합니다.
    -->
    <component
    v-bind:is="currentTabComponent"
    class="tab" ></component>
  </div>
</template>
<script>

export default {

  data() {
     const currentTab = "Home";
     const tabs = ['Home', 'Posts', 'Archive'];
    return {currentTab, tabs }
  },
  components : {
      tabHome : {
        template : "<div>Home component</div>"
      },
      tabPosts : {
        template : '<div>Posts component</div>'
      },
      tabArchive : {
        template : '<div>Archive component</div>'
      }
  },
  computed: {
    currentTabComponent : function(){
      console.log( "currentTabComponent:", this.currentTab.toLowerCase()  )
      return 'tab-' + this.currentTab.toLowerCase();
    }
  }

}

</script>

<style>
.tab-button {
  padding: 6px 10px;
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
  border: 1px solid #ccc;
  cursor: pointer;
  background: #f0f0f0;
  margin-bottom: -1px;
  margin-right: -1px;
}
.tab-button:hover {
  background: #e0e0e0;
}
.tab-button.active {
  background: #e0e0e0;
}
.tab {
  border: 1px solid #ccc;
  padding: 10px;
}
</style>
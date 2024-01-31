<script>

import { ref, watchEffect } from 'vue'

export default{
  setup(props) {
    const API_URL = `https://api.github.com/repos/vuejs/core/commits?per_page=3&sha=`

    const branches = ['main', 'v2-compat']
    const currentBranch = ref(branches[0])
    const commits = ref(null)

    watchEffect(async () => {
      /*
      종속성 추적 방식:
          watchEffect:  콜백 함수 내에서 사용된 모든 reactive 속성들을 자동으로 추적하고 
                        해당 속성들이 변경될 때마다 콜백 함수를 다시 실행합니다. 
                        즉, 콜백 함수에서 사용된 reactive 속성이 자동으로 종속성으로 등록됩니다.
          
          watch:        명시적으로 관찰할 속성을 지정해야 하며, 
                        해당 속성이 변경될 때만 콜백 함수를 실행합니다. 
                        특정 속성에 대한 종속성을 명시적으로 정의해야 합니다.
      
      콜백 함수의 형태:
          watchEffect:  콜백 함수는 reactive 속성 변경 시마다 실행되며, 
                        변경된 값을 매개변수로 받습니다. 종속성이 변경될 때마다 콜백 함수 전체가 실행됩니다.
          
          watch:        콜백 함수는 변경된 값과 이전 값 두 개의 인자를 받습니다. 
                        종속성이 변경되었을 때만 콜백 함수가 실행됩니다.
      
      명시적/암묵적 종속성 등록:
          watchEffect:  암묵적으로 콜백 함수 내에서 사용된 모든 reactive 속성을 종속성으로 등록합니다.
          
          watch:        명시적으로 종속성을 등록해야 하며, 
                        종속성 목록에 추가된 속성들만 변경 시 콜백 함수가 실행됩니다.
      */
      // this effect will run immediately and then
      // re-run whenever currentBranch.value changes
      const url = `${API_URL}${currentBranch.value}`
      commits.value = await (await fetch(url)).json();
      console.log(commits.value);
    })

  return { branches, currentBranch,  }
  }
}
</script>

<template>
  <div>
   <template v-for="branch in branches">
      <input type="radio"
        :id="branch"
        :value="branch"
        name="branch"
        v-model="currentBranch"
        >{{ branch  }}
   </template>

  </div>
</template>


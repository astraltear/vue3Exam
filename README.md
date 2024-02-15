npx와 npm은 둘 다 Node.js 패키지 매니저(NPM)와 관련된 도구이지만 목적과 사용 방법에서 차이가 있습니다.

npm (Node Package Manager):

패키지를 설치하고 의존성을 관리하는 주요 도구입니다.
npm install [패키지명]과 같이 사용하여 패키지를 로컬 또는 전역으로 설치합니다.
주로 프로젝트의 의존성을 관리하는 데 사용됩니다.

npx (Node Package eXecute):

로컬에 설치된 패키지를 실행하거나, npm 레지스트리에서 패키지를 다운로드하여 일회성으로 실행하는 데 사용됩니다.
로컬에 설치하지 않고도 패키지를 실행할 수 있으므로 일회성 명령어를 실행할 때 특히 유용합니다.
주로 글로벌로 설치하지 않고 최신 버전의 패키지를 사용할 때 활용됩니다.
간단한 예시로 설명하면, Vue.js 프로젝트를 생성하는데:

npm install -g create-vue: create-vue 패키지를 글로벌로 설치합니다.

npx create-vue: 로컬에 create-vue를 설치하지 않고 최신 버전으로 프로젝트를 생성합니다.


# 참고 npx로 간단한 웹 서버 띄위기
npx local-web-server

# vue3 examples

## vue 프로젝트 만들기 1
## vue cli설치
npm install -g @vue/cli
vue create my-vue3-project

## vite cli설치
npm install -g create-vite
create-vite my-vue3-project

## vue 프로젝트 만들기 2
## vite로 설치하는 방법
npx create-vite

## vue 프로젝트 만들기 3
## npx로  vue생성 
npx create-vue


## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

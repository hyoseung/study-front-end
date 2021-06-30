# Storybook

## Storybook

* UI 컴포넌트를 직접 보면서 개발할 수 있는 환경을 제공하는 툴
* 실제 프로젝트 내에서 실행되는 것이 아니라 독립된 환경으로 실행

## 설치

```bash
npx sb init --type vue

// vue2 -> --type vue
// vue3 -> --type vue3
```

### package.json

```javascript
{
  ...
  "scripts": {
    "storybook": "start-storybook -p 6006",
    "build-storybook": "build-storybook"
  },
  "dependencies": {
    ...
  },
  "devDependencies": {
    "@babel/core": "^7.14.6",
    "@storybook/addon-actions": "^6.3.1",
    "@storybook/addon-essentials": "^6.3.1",
    "@storybook/addon-links": "^6.3.1",
    "@storybook/vue": "^6.3.1",
    "babel-loader": "^8.2.2",
    "vue-loader": "^15.9.7",
    ...
  }
}

```

### .storybook 폴더 생성

### src &gt; stories 폴더 생성

## 실행

```bash
# Starts Storybook in development mode
yarn storybook
npm run storybook
```

## npx

* npm의 5.2.0 버전부터 새로 추가된 도구
* npm 레지스트리에 올라가있는 패키지를 쉽게 설치하고 관리할 수 있도록 도와주는 CLI 도구
* which npx : 명령어를 실행하면 npm 버전에 이미 설치되어 있는지 확인 가능
* npm = Package Manager \(관리\), npx = Package Runner \(실행\)
* 참고 : [https://webruden.tistory.com/275](https://webruden.tistory.com/275)

## 출처

* [Storybook 공식사이트](https://storybook.js.org/)
* [Storybook 공식사이트 - Vue](https://storybook.js.org/docs/vue/get-started/introduction)
* [캡틴.JS \| 2020. 3. 17. 13:13 \| \[vue.js\] vue+storybook 적용하기](https://avengersrhydon1121.tistory.com/272)


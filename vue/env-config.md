# 환경변수 설정

## 실행모드

* vue application이 실행되는 모드
* 3가지 모드 제공 : `development`, `production`, `test`
* 사용자 정의 모드도 추가 가능

### package.json

```javascript
// package.json
...
"scripts": {
    "serve": "vue-cli-service serve", // vue-cli-service serve --mode development
    "build": "vue-cli-service build", // vue-cli-service build --mode production
    "lint": "vue-cli-service lint"
  },
...
```

#### 사용자 정의 모드

* vue-cli-service serve --mode \[사용자 정의 모드명]

```javascript
// package.json
...
"scripts": {
    "serve": "vue-cli-service serve --mode local",
    "build": "vue-cli-service build --mode prod",
    "lint": "vue-cli-service lint"
  },
...
```

## 환경변수

* 실행 모드에 따라 선택되는 변수
* 기본적으로 2개의 환경 변수 제공 : `NODE_ENV`, `BASE_URL`
* 환경변수들은 `process.env 객체`에 정의 되어 있음

### 기본 제공 환경변수

#### NODE_ENV

* 앱이 실행되는 모드
* 기본 모드 : `development`, `production`, `test`
* 사용자 정의 모드 추가 가능

#### BASE_URL

* vue.config.js의 publicPath 옵션에 해당
* 앱이 배포되는 기본 경로

### 사용자 정의

* 만약 실행모드명이 `local`일 경우
* .evn.local 파일 생성

```javascript
NODE_ENV = "local"
BASE_URL: "/"

VUE_APP_NAME = "홍길동"
```

### 주의사항

#### 환경 변수 파일 위치

root 디렉토리에 위치해야함

#### 환경 변수 이름

새로운 환경변수를 추가할 때 `VEU_APP_` 으로 시작해야 인식됨

#### .env.local

만약 실행 모드명을 `local`로 할 경우 .gitignore 수정해야함

.env.local 파일은 기본적으로 제외되어 있음

## Vue에 적용 예

API 호출 시 baseURL이 `development`와 `production`일 때 다름

환경변수로 실행모드별로 baseURL 적용

```javascript
// .env.development
NODE_ENV = "development"
VUE_APP_API_BASE_URL = "http://localhost:8081"
```

```javascript
// .env.production
NODE_ENV = "production"
VUE_APP_API_BASE_URL = "http://52.79.197.236:8081"
```

```javascript
// axios 설정 파일

import axios from 'axios';

const instance = axios.create({
  baseURL: process.env.VUE_APP_API_BASE_URL
})
```

만약 실행모드와 상관없이 공통으로 사용자 정의 환경변수 사용할 때

```javascript
// .env

VUE_APP_COMMON_TEST = "common test"
```

`console.log(process.env);` 로 호출해본 결과

![](<../.gitbook/assets/image (34).png>)

## 출처

* vue.config.js : [https://cli.vuejs.org/config/#global-cli-config](https://cli.vuejs.org/config/#global-cli-config)
* [skyepodium | 2020년 4월 15일 | vue 실행모드와 환경변수 설정](https://velog.io/@skyepodium/vue-%EC%8B%A4%ED%96%89-%EB%AA%A8%EB%93%9C%EC%99%80-%ED%99%98%EA%B2%BD-%EB%B3%80%EC%88%98-%EC%84%A4%EC%A0%95)

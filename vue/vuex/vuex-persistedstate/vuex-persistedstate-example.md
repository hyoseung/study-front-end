# 예제

`vuex-persistedstate`, `js-cookie`를 이용한 개발과 이슈 공유

```javascript
// store/index.js

import Vue from "vue";
import Vuex from "vuex";

import createPersistedState from "vuex-persistedstate";
import * as Cookies from "js-cookie";

import login from "./modules/login.js";
import test from "./modules/test.js";

Vue.use(Vuex);

export default new Vuex.Store({
  plugins: [
    createPersistedState({
      key: "user",
      paths: ["login"],
      storage: {
        getItem: key => return Cookies.get(key)
        setItem: (key, value) => {
          let date = new Date();
          let day = 24 * 60 * 60 * 1000;
          date.setTime(date.getTime() + day);
          return Cookies.set(key, value, { expires: date, secure: false });
        },
        removeItem: key => Cookies.remove(key)
      }
    })
  ],
  modules: {
    login,
    test
  }
});

```

```javascript
// store/modules/login.js

import * as Cookies from "js-cookie";

export default {
  namespaced: true,
  state: {
    user: null,
    connectionTime: new Date()
  },
  getters: {
    ...
  },
  mutations: {
    setUserInfo(state, payload) {
      state.user = payload.user;
      state.loginPathName = payload.loginPathName;
      state.connectionTime = new Date();
    }
  },
  actions: {
    ...
  }
};

```

로그인 후 응답 결과를 login 모듈에 저장하는 코드 작성

#### `key`

* cookie에 저장될 key 값 설정
* 기본값은 vuex

#### `paths`

* paths를 지정하지 않으면 vuex에 설정된 state가 모두 저장됨
* 만약 특정 모듈만 저장하고 싶을 때 paths에 모듈명을 적어야함 ex\) `paths: ['login']`
* 모듈의 특정 state만 cookie에 저장하고 싶을 경우 `모듈명.state명` 으로 적어야함  ex\) `paths: ['login.user']`




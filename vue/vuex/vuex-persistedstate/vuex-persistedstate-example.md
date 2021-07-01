---
description: 'vuex-persistedstate, js-cookie를 이용한 개발과 이슈 공유'
---

# 예제

## 코드

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

#### `storage`

* 새로고침 시 getItem를 통해 cookie에 저장된 값을 가져옴
* vuex에 `mutation`이 호출되면 setItem을 호출함

## 이슈

`test 모듈`에서 `mutation`이 호출되면 `storage > setItem`이 호출되어 `login 모듈`에 `state`를 `cookie`에 저장합니다. `paths: ['login']`을 설정과는 별도로 `login 모듈`에 `state`가 변경되었을때만 `storage > setItem`을 호출하도록 코드를 수정해야 합니다.

vuex-persistedstate에서 filter를 제공하는데, 기본값은 true입니다. mutations이 호출되면 filter가 동작합니다. 이 때 파라미터를 통 `{ payload: "", type: "모듈명/mutation명" }` object를 받을 수 있습니다. 특정 `mutation`이 호출되었을 때만 `setItem`이 호출 될 수 있도록 아래 조건문을 추가했습니다. `true`일 때는 `setItem`을 호출하고, `false`면 `setItem`을 호출하지 않습니다.

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
      filter: mutation => {
        if (mutation.type === "login/setUserInfo") {
          return true;
        }
        return false;
      },
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


# cookie 사용

## 설치

기본적으로 localStorage를 사용하지만 cookie에 저장하고 싶을 경우 아래와 같이 설정한다.

```
yarn add js-cookie
```

## vuex plugin 설정

```javascript
import { Store } from "vuex";
import createPersistedState from "vuex-persistedstate";
import * as Cookies from "js-cookie";

const store = new Store({
  // ...
  plugins: [
    createPersistedState({
      storage: {
        getItem: (key) => Cookies.get(key),
        // Please see https://github.com/js-cookie/js-cookie#json, on how to handle JSON.
        setItem: (key, value) =>
          Cookies.set(key, value, { expires: 3, secure: true }),
        removeItem: (key) => Cookies.remove(key),
      },
    }),
  ],
});
```

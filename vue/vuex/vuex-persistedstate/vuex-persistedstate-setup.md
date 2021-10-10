# 설정

## vuex plugin 설정

### vuex-persistedstate 3.x (for Vuex 3 and Vue 2)

```javascript
// store/index.js

import Vuex from "vuex";
import createPersistedState from "vuex-persistedstate";

const store = new Vuex.Store({
  // ...
  plugins: [createPersistedState()],
});
```

### vuex-persistedstate 4.x (for Vuex 4 and Vue 3)

```javascript
// store/index.js

import { createStore } from "vuex";
import createPersistedState from "vuex-persistedstate";

const store = createStore({
  // ...
  plugins: [createPersistedState()],
});
```

## options

### `createPersistedState([options])`

{% embed url="https://github.com/robinvdvleuten/vuex-persistedstate#api" %}


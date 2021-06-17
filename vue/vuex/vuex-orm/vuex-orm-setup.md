# 설정

## 폴더 구조

![](../../../.gitbook/assets/image.png)

## Define Models

### index.js

```javascript
import Order from './orm/Order';
import Detail from './orm/Detail';
import Delivery from './orm/Delivery';

export {
  Order,
  Detail,
  Delivery
}
```

### 각 Model

일단 아래와 같은 코드로 Model 생성

```javascript
import { Model } from '@vuex-orm/core'

export default class Order extends Model {
  // This is the name used as module name of the Vuex Store.
  static entity = 'order'

  // List of all fields (schema) of the post model. `this.attr` is used
  // for the generic field type. The argument is the default value.
  static fields () {
    return {
      id: this.attr(null),
      name: this.attr(''),
      email: this.attr('')
    }
  }
}
```

## Register Models to Vuex

store &gt; index.js

```javascript
import Vue from 'vue'
import Vuex from 'vuex'

import VuexORM from '@vuex-orm/core'
import * as models from '@/models';

Vue.use(Vuex)

// Create a new instance of Database.
const database = new VuexORM.Database()

// Register Models to Database.
database.register(models.Order);
database.register(models.Detail);
database.register(models.Delivery);

// Create Vuex Store and register database through Vuex ORM.
export default new Vuex.Store({
  plugins: [VuexORM.install(database)]
})

```




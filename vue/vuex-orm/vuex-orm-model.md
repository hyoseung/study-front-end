# Model

## 예제 데이터 구조

* Order &lt;- 1 ------- N -&gt; Detail
* Detail &lt;- 1 ------- 1 -&gt; Delivery

주문에 상세 주문\(주문한 품목들\)이 있고, 각 상세 주문이 서로 다른 배송지로 간다고 생각해서 각 상세 주문에 배송지를 1:1로 매핑 함.

## Entity Name

* `static entity` 는 state 키로 사용됨
* database의 table 명이라고 생각할 수 도 있음
* state는 Vuex ORM에서 자동으로 생성함
* `store.state.entities.[entity name]` 로 접근 할 수 있음
  * `store.state.entities.orders` 

```javascript
import { Model } from '@vuex-orm/core'

export default class Order extends Model {
  // This is the name used as module name of the Vuex Store.
  static entity = 'orders'

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

## Fields

* `static fields` 는 데이터의 스키마를 반환해야함
* database의 column 명이라고 생각하면 됨
* fields type은 `this.attr()`로 정할 수 있음

## Field Attributes

### Generic Type

* 기본값을 세팅할 수 있음

```javascript
import { Model } from '@vuex-orm/core'

export default class Test extends Model {
  ...
  static fields () {
    return {
      id: this.attr(null),
      name: this.attr('홍길동'),
      rand: this.attr(() => Math.random())
    }
  }
}
```

### Primitive Types

*  `this.string()`, `this.number()`, `this.boolean()` 사용 가능
* null을 허용하고 싶을때는 .nullable\(\)

```javascript
import { Model } from '@vuex-orm/core'

export default class Test extends Model {
  ...
  static fields () {
    return {
      name: this.string(null).nullable(),
    }
  }
}
```

### UID Type

* `this.uid()` 고유 ID를 생성 \(문자열\)

```javascript
import { Model } from '@vuex-orm/core'

export default class Test extends Model {
  ...
  static fields () {
    return {
      id: this.uid(), // $uid32
    }
  }
}
```

## Primary Key

* Vuex ORM은 `id` 라는 기본키가 있다고 가정함
* `static primaryKey` 로 id를 재정의 할 수 있음

```javascript
import { Model } from '@vuex-orm/core'

export default class Test extends Model {
  ...
  static primaryKey = 'testId' // 단일
  static primaryKey = ['testId', ''] // 복합키
  ...
  static fields () {
    return {
      testId: this.string(null),
    }
  }
}
```


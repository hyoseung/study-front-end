# Model Relationships

* Relationship Management는 vuex-orm의 강점
* 관계는 Model의 static fields에서 attribute로 정의할 수 있음
* 자세한 설명은 [공식 문서 참고](https://vuex-orm.org/guide/model/relationships.html#one-to-one) \(예제에 적용한 관계 위주로 설명\)

## 예제 데이터 구조

* Order &lt;- 1 ------- N -&gt; Detail
* Detail &lt;- 1 ------- 1 -&gt; Delivery

주문에 상세 주문\(주문한 품목들\)이 있고, 각 상세 주문이 서로 다른 배송지로 간다고 생각해서 각 상세 주문에 배송지를 1:1로 매핑 함.

## OneToMany

* `this.hasMany()`
* 첫번째 인수 : the related model
* 두번째 인수 : the 'foreign key' of the related model
* 세번째 인수 : override which id to look up on parent model

```javascript
// Order.js
import { Model } from '@vuex-orm/core'
import Detail from './Detail';

export default class Order extends Model {
  static entity = 'order'
  static primaryKey = 'orderId'

  static fields () {
    return {
      orderId: this.number(null),
      orderNo: this.string(null).nullable(),
      name: this.string(null).nullable(),
      phone: this.string(null).nullable(),
      paymentType: this.string(null).nullable(), // 결제방법 (카드, 무통장입금)
      details: this.hasMany(Detail, 'orderId')
    }
  }
}
```

```javascript
// Detail.js
import { Model } from '@vuex-orm/core'

export default class Detail extends Model {
  static entity = 'detail'
  static primaryKey = 'detailId'

  static fields () {
    return {
      detailId : this.number(null),
      itemCode: this.string(null).nullable(),
      itemName: this.string(null).nullable(),
      itemCategory: this.string(null).nullable(), // 품목카테고리 (패션, 뷰티, 식품, 생필품, 디지털)
      quantity: this.number(0),
      price: this.number(0),
      orderId: this.number(null)
    }
  }
}
```

## OneToOne

* `this.hasOne()`
* 첫번째 인수 : the related model
* 두번째 인수 : the 'foreign key' of the related model
* 세번째 인수 : id값 이외에 사용자 지정키를 지정할 때

```javascript
// Detail.js
import { Model } from '@vuex-orm/core'
import Delivery from './Delivery';

export default class Detail extends Model {
  static entity = 'detail'
  static primaryKey = 'detailId'

  static fields () {
    return {
      detailId : this.number(null),
      itemCode: this.string(null).nullable(),
      itemName: this.string(null).nullable(),
      itemCategory: this.string(null).nullable(), // 품목카테고리 (패션, 뷰티, 식품, 생필품, 디지털)
      quantity: this.number(0),
      price: this.number(0),
      orderId: this.number(null),
      deliveryIdTest: this.number(null),
      delivery: this.hasOne(Delivery, 'deliveryId', 'deliveryIdTest')
    }
  }
}
```

```javascript
// Delivery.js
import { Model } from '@vuex-orm/core'

export default class Delivery extends Model {
  static entity = 'delivery'
  static primaryKey = 'deliveryId'

  static fields () {
    return {
      deliveryId: this.number(null),
      address: this.string(null).nullable(),
      addressDetail: this.string(null).nullable(),
      post: this.string(null).nullable()
    }
  }
}
```






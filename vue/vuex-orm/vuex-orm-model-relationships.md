# Model Relationships

자세한 설명은 [공식 문서 참고](https://vuex-orm.org/guide/model/relationships.html#one-to-one)

예제에 적용한 관계 위주로 설명

## 예제 데이터 구조

* Order &lt;- 1 ------- N -&gt; Detail
* Detail &lt;- 1 ------- 1 -&gt; Delivery

주문에 상세 주문\(주문한 품목들\)이 있고, 각 상세 주문이 서로 다른 배송지로 간다고 생각해서 각 상세 주문에 배송지를 1:1로 매핑 함.

## OneToMany






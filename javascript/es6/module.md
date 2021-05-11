# 모듈 \(Module\)

* 기존의 자바스크립트에서는 모듈화를 통한 분리가 불가능했음
* ES6부터는 `export`, `import` 키워드로 모듈화 구현이 가능하게 됨

## Named Export

이름을 지정해서 export 하는 방법이다. import 할때도 해당 이름을 사용

### 초기화와 동시에 export

```javascript
export const name = '홍길동';
export function sum(a, b) {
  return a+b;
}
```

### 선언된 객체의 export

```javascript
const name = '홍길동';
const sum = function(a, b) {
  return a+b;
}

export { name, sum };
```

### 별칭 지정

```javascript
const name = '홍길동';
const sum = function(a, b) {
  return a+b;
}

export { name, sum as sumNumber };
```

### 다른 모듈의 객체 `export`

* 다른 모듈에서 `import` 해옴과 동시에 `export` 해버리는 방식
* 자주 사용되지는 않지만 여러 모듈을 묶어서 다시 `export`하는 `index.js`같은 파일을 만들 때 사용

```javascript
export { name, sum } from '경로/파일';
```

## Default Export

* 모듈 당 한번만 할 수 있는 export default
* `var`, `let`, `const`를 바로 export default 할 수 없음
* 초기화와 동시에 export 불가능, 미리 선언된 변수, 함수, 익명함수를 export 할 수 있

```javascript
export default name;
export default const name; // 사용할 수 없음

export default function() { ... }
export default sum;
```

* as default를 사용하여 default가 아닌 다른값과 함께 export할 수 있음

```javascript
export { sum as default, name, age }
```

## Import

* Named Export

```javascript
import { name, sum } from './module.js';

// as를 사용하여 별칭을 지정할 수 있
import { sum as sumNumber } from './module.js';

import * as module from './module.js';
module.name
model.sum(1,2)
```

* Default Export

```javascript
// export default
// export { sum as default, name, age }
import sum from './module.js';
import sum, { name, age } from './module.js';
```


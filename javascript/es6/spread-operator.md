# 전개 연산자 \(spread operator\)

## ES5

```javascript
var number = [1,2,3];
var name = ['a', 'b'];
var color = "red";

var result = number.concat(name, color);

console.log(result); // [ 1, 2, 3, 'a', 'b', 'red' ]
```

## ES6

```javascript
let number = [1,2,3];
let name = ['a', 'b'];
let color = "red";

let result = [...number, ...name, color];

console.log(result); // [ 1, 2, 3, 'a', 'b', 'red' ]
```

### 새로운 배열 생성

* 전개 연산자 사용 X
  * number와 result는 동일 주소값을 참조하고 있음

```javascript
let number = [1,2,3];

let result = number.reverse();

console.log(number === result); // true
console.log(number); // [ 3, 2, 1 ]
console.log(result); // [ 3, 2, 1 ]
```

* 전개 연산자 사용
  * number와 result는 서로 다른 주소값을 참조하고 있음 \(서로 다른 객체\)

```javascript
let number = [1,2,3];

let result = [...number].reverse();

console.log(number === result); // false
console.log(number); // [ 1, 2, 3 ]
console.log(result); // [ 3, 2, 1 ]
```

### 비구조화 할당 \(구조분해할당\)

```javascript
let number = [1,2,3,4,5];

let [a, b, ...rest] = number;

console.log(a); // 1
console.log(b); // 2
console.log(rest); // [3, 4, 5]
```




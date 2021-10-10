# 향상된 객체 리터럴 (enhanced object literals)

## ES5

```javascript
let name = '홍길동';
let age = 30;

let obj = {
  name: name,
  age: age
}

console.log(obj);
//{name: "홍길동", age: 30}
```

## ES6

### 단축된 프로퍼티 초기화

객체의 속성을 작성할 때, 변수명과 동일하면 생략 가능

```javascript
let name = '홍길동';
let age = 30;

let obj = {
  name,
  age
}

console.log(obj);
//{name: "홍길동", age: 30}
```

### 간결한 메서드

`function` 키워드 생략가능

```javascript
let person = {
  name: '홍길동',
  getName() { // getName: function() { ... }
    return this.name;
  }
}
```

## Vue

```javascript
// Vue

export default {
  components: {
    ButtonComponent
  },
  data() {
    return {...}
  },
  methods: {
    getName() { ... }
  }
}
```

# 화살표 함수 \(Arrow Function\)

## ES5

```javascript
var a = function() {
  console.log("function");
}
a();
```

## ES6

### `function` 키워드의 축약형

```javascript
const a = () => {
  console.log("arrow function");
}
a();
```

### 괄호와 `return` 생략 가능

#### 파라미터를 1개만 받을 때 괄호 생략 가능

```javascript
const print = text => {
  console.log(text);
}

print('test'); // test
```

#### 간단한 표현식을 반환할 때 괄호와 `return` 생략 가능

```javascript
const sum = (a, b) => (a + b);

console.log(sum(1, 2)); // 3
```

### `this`를 `bind` 하지 않는다

#### this

대부분의 this의 값은 함수를 호출한 방법이 결정 

| 상황 | this |
| :--- | :--- |
| global scope | 전역 객체 \(Window 객체\) |
| 함수 | 전역 객체 \(Window 객체\) |
| 객체에 속한 메소드 | 메소드가 속한 객체 |
| 객체에 속한 메소드의 내부함수 | 전역 객체 \(Window 객체\) |
| 생성자 | 생성자로 인해 생성된 새로운 객체 |

{% hint style="info" %}
* 함수 : 자바스크립트 내장 객체인 Function 생성자로 생성된 객체
* 메소드 : Function 내장 객체로 생성된 함수가 객체의 프로퍼티가 될 때
{% endhint %}

함수가 호출하는 방법이 `this` 값을 결정하기 때문에 `person.test()`는 함수호출을 `person`이 했기때문에 `this`는 `person객체`고, `aaa()`는 함수 호출을 전역객체에서 하고있기 때문에 `this`는 `Window 객체`가 됨

```javascript
let person = {
  name: '홍길동',
  age: 30,
  test: function() {
    console.log(this);
  }
};

person.test(); // person 객체, {name: "홍길동", age: 30, test: ƒ}

let aaa = person.test;
aaa(); // Window 객체
```

#### ES5 - bind

함수를 어떻게 호출했는지 상관하지 않고 this 값을 설정할 수 있는 bind 메서드를 도입

```javascript
const account = {
  username: "홍길동",
  balance: 10000,
  getBalance: function() {
    innerFunc = function() {
      console.log(this === window); // true
      return `${this.username}님의 잔액은 ${this.balance}입니다.`;
    };
    console.log(innerFunc());
  }
};

account.getBalance(); //undefined님의 잔액은 undefined입니다.
```

* bind 사용

```javascript
const account = {
  username: "홍길동",
  balance: 10000,
  getBalance: function() {
    innerFunc = function() {
      console.log(this === window); // false
      return `${this.username}님의 잔액은 ${this.balance}입니다.`;
    }.bind(this);
    console.log(innerFunc());
  }
};
account.getBalance(); //홍길동님의 잔액은 10000입니다.
```

#### ES6 - 화살표 함수

* 화살표 함수는 자신만의 this 를 갖지 않기 때문에, 바깥 스코프에서 this 의 값을 계승받음
* 이러한 특징 때문에 객체의 메소드로 화살표 함수를 사용하는 것은 적합하지 않음

```javascript
const account = {
  username: "홍길동",
  balance: 10000,
  getBalance: function() {
    //화살표 함수 사용
    innerFunc = () => `${this.username}님의 잔액은 ${this.balance}입니다.`;
    console.log(innerFunc());
  }
};
account.getBalance(); //홍길동님의 잔액은 10000입니다.
```

## Vue




# let과 const

## ES5

### var

* ES6 이전의 자바스크립트에서는 `var` 키워드를 통해 변수를 선언
* function scope

```javascript
function foo() {
  if (true) {
    var a = 'bar';
  }

  // function scope 이므로 접근 가
  console.log(a);
}

foo(); // outpu : 'bar'
```

## ES6

### let

* 중복 선언 허용 X
* block scope : 중괄호 ({}) 기준으로 유효범위 갖음

```javascript
function foo() {
  if (true) {
    let a = 'bar';
  }

  console.log(a);
}

foo(); // output : a is not defined
```

### const

* 상수 기능
* block scope

```javascript
const a = 'test'
```

## 호이스팅 (Hoisting)

자바스크립트 함수는 실행되기 전에 함수 안에 필요한 변수값들을 모두 모아서 유효 범위의 최상단에 선언

### 변수 생성 3단계

1. **선언 단계(Declaration Phase)**: 변수를 변수 객체(Variable Object)에 등록합니다. 이 변수 객체는 스코프가 참조하는 대상이 됩니다.
2. **초기화 단계(Initialization Phase)**: 변수 객체(Variable Object)에 등록된 변수를 위한 공간을 메모리에 확보합니다. 이 단계에서 변수는 `undefined`로 초기화됩니다.
3. **할당 단계(Assignment Phase)**: `undefined`로 초기화된 변수에 실제 값을 할당합니다.

### 호이스팅 대상

* `var` 키워드, `함수 선언문`에서 호이스팅 발생
* `var` 키워드 선언만 끌어올려지고, 할당은 끌어 올려지지않음 -> `undefined`
* `let` / `const`키워드와 `함수 표현식`에서는 호이스팅 되지 않음

| var                                   | let, const                            |
| ------------------------------------- | ------------------------------------- |
| 선언단계 + 초기화 단계 한번에 호이스팅 -> `undefined` | 선언단계 호이스팅 -> 참조 에러(ReferenceError) 발생 |

### 호이스팅 우선순위

변수 선언이 함수 선언보다 높은 우선순위를 가짐

### 예제

```javascript
console.log("hello");
var color = "yellow"; // var 변수 
let fruit = "apple"; // let 변수

// 호이스팅 결과
var color; // (호이스팅)
console.log("hello");
color = "yellow";
let fruit = "apple";
```

```javascript
hello(); // output: hello
bye(); // output: bye is not a function
hi(); // output: Cannot access 'hi' before initialization

function hello() {
  console.log('hello');
}

var bye = function() {
  console.log('bye');
}

let hi = function() {
  console.log('hi');
}

// 호이스팅 결과
var bye; // (호이스팅)
function hello() { // (호이스팅) - 함수선언
  console.log('hello');
}

hello();
bye();
hi();

bye = function() {
  console.log('bye');
}

let hi = function() { // 호이스팅X - let, 함수표현식
  console.log('hi');
}
```

## 출처

* [holim0 | 2021년 1월 2일 | Front-End 면접 질문 대비 Part1 (hoisting, closure, this)](https://velog.io/@holim0/Front-End-%EB%A9%B4%EC%A0%91-%EC%A7%88%EB%AC%B8-%EB%8C%80%EB%B9%84-Part1-hoisting-closure-this)

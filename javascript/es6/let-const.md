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

* 호이스팅 X
* 중복 선언 허용 X
* block scope : 중괄호 \({}\) 기준으로 유효범위 갖음

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

## 호이스팅 \(Hoisting\)

자바스크립트 함수는 실행되기 전에 함수 안에 필요한 변수값들을 모두 모아서 유효 범위의 최상단에 선언

* `var` 변수 선언과 `함수 선언문`에서 호이스팅 발생
* var 변수/함수의 선언만 위로 끌어 올려지며, 할당은 끌어 올려지지않음
* `let` / `const`변수 선언과 `함수 표현식`에서는 발생 안함

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


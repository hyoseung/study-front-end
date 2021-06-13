# this 키워드

## this란?

* this는 자바스크립트 런타임 시에 바인딩이 이루어지는 실행 컨텍스트 중 하나
* this는 호출 시점에서 실행함수가 가리키는 객체
* 해당 함수가 실행되는 동안에 사용할 수 있음
*  복잡한 코드에서 암시적 바인딩에 의해 혼란스러운 경우가 많은데, 이런 문제를 해결하기 위해서 call이나 apply 같은 내장 유틸리티를 사용하여 명시적으로 바인딩을 해줌

## this 결정

대부분의 this의 값은 함수를 호출한 방법이 결정

| 상황 | this |
| :--- | :--- |
| global scope | 전역 객체 \(Window 객체\) |
| 함수 | 전역 객체 \(Window 객체\) |
| 객체에 속한 메소드 | 메소드가 속한 객체 |
| 객체에 속한 메소드의 내부함수 | 전역 객체 \(Window 객체\) |
| 생성자 | 생성자로 인해 생성된 새로운 객체 |

> * 함수 : 자바스크립트 내장 객체인 Function 생성자로 생성된 객체
> * 메소드 : Function 내장 객체로 생성된 함수가 객체의 프로퍼티가 될 때

## 명시적 지

### bind

함수가 가리키는 this 만 바꾸고 실행시키지않음

```javascript
func.bind(thisArg[, arg1[, arg2[, ...]]])

thisArg: 바인딩 함수가 타겟 함수의 this에 전달하는 값
arg1, arg2, ...: func이 호출되어야 하는 인수
```

### call

this를 바인딩하고 함수를 호출하고 실행시킴

```javascript
func.call(thisArg[, arg1[, arg2[, ...]]])

thisArg: func 호출에 제공되는 this의 값
arg1, arg2, ...: func이 호출되어야 하는 인수
```

### apply

call과 비슷하지만만 인자 전달을 배열로 해줌

```javascript
fun.apply(thisArg, [argsArray])

thisArg: func 호출에 제공되는 this의 값
argsArray: func이 호출되어야 하는 인수를 지정하는 유사 배열 객체
```

## 참고

* [https://medium.com/@lidiach217/javascript-this-%ED%82%A4%EC%9B%8C%EB%93%9C-eb4e01313615](https://medium.com/@lidiach217/javascript-this-%ED%82%A4%EC%9B%8C%EB%93%9C-eb4e01313615)
* [https://velog.io/@josworks27/%ED%95%A8%EC%88%98%ED%98%B8%EC%B6%9C-call-apply-bind-%EC%B0%A8%EC%9D%B4](https://velog.io/@josworks27/%ED%95%A8%EC%88%98%ED%98%B8%EC%B6%9C-call-apply-bind-%EC%B0%A8%EC%9D%B4)
* [https://wooooooak.github.io/javascript/2018/12/08/call,apply,bind/](https://wooooooak.github.io/javascript/2018/12/08/call,apply,bind/)






# 클로저(Closure)

## 클로저란?

외부 함수의 호출이 종료되더라도, 반환된 내부함수가 자신이 선언되었을 때의 환경(Lexical environment)인 스코프를 기억하여, 외부에서(선언될 당시 환경이 아닌 곳에서) 호출되어도 그 환경(스코프)에 접근할 수 있는 함수.

자유 변수 : 내부함수에서 사용하는 외부함수의 변수

어떤함수 A에서 선언한 변수 C를 참조하는 내부함수 B를 외부로 전달하는 경우, 내부함수 B가 선언될 당시의 환경을 기억하고 있기 때문에 함수 A의 실행 컨텍스트가 종료되어도 변수 C에 접근 할 수 있는 것을 의미

## 예시

```javascript
function outerFunc() {
  var x = 1; // 자유변수
  var innerFunc = function() {  // 클로저
    console.log(x);
  }
  return innerFunc;
}

var test = outerFunc();
test();
```

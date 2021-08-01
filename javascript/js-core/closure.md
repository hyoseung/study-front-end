# 클로저\(Closure\)

## 클로저란?

외부 함수의 호출이 종료되더라도, 반환된 내부함수가 자신이 선언되었을 때의 환경\(Lexical environment\)인 스코프를 기억하여, 외부에서\(선언될 당시 환경이 아닌 곳에서\) 호출되어도 그 환경\(스코프\)에 접근할 수 있는 함수.

자유 변수 : 내부함수에서 사용하는 외부함수의 변수

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


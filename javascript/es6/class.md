# class

## ES5

* 자바스크립트는 `prototype` 기반 언어
* 공식적으로 클래스라는 개념이 존재하지 않았음
* 함수를 사용하여 객체를 정의
* 객체의 메서드를 정의할 때 `prototype`안에 직접 정의

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.print = function() {
  console.log(this.name + "의 나이는 " + this.age + "살 입니다.");
}

var p1 = new Person("홍길동", 30);
p1.print(); // 홍길동의 나이는 30살 입니다.
```

## ES6

* ES6에서는 `class` 문법을 만들었음
* 자바스크립트의 객체 모델이 바뀐것이 아니므로 내부에서는 그대로 `prototype` 기반으로 작동
* `Syntactic sugar`(문법적 설탕) : 내부 동작은 동일하지만, 구현 방식에 맞춘 새로운 문법

```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  print() {
    console.log(this.name + "의 나이는 " + this.age + "살 입니다.");
  }
}

var p1 = new Person("홍길동", 30);
p1.print(); // 홍길동의 나이는 30살 입니다.
```

## 참고

* [afant | 2019년 4월 21일 | \[Javascript\] 꼭 알아야 할 Prototype의 개념](https://velog.io/@afant/Javascript-%EA%BC%AD-%EC%95%8C%EC%95%84%EC%95%BC-%ED%95%A0-Prototype%EC%9D%98-%EA%B0%9C%EB%85%90-)

# 불변성

## 불변성 이란?

* 사전적의미는 변하지않는 성질
* 즉, 메모리 영역에서 값을 변경할 수 없다는 의미

## 원시타입과 참조타입

### 원시타입 (primitive type)

* Boolean
* String
* Number
* undefined
* Null
* Symbol

원시타입은 불변하다. 이 값은 메모리영역 안에서 변경이 불가능하며 변수에 할당할 때 완전히 새로운 값이 만들어져 재할당된다.

```javascript
let name = '김철수';
name = '홍길동';

// name이라는 변수명은 동일하지만 '김철수'와 '홍길동'이 할당된 메모리영역은 서로 다르다.
```

### 참조타입 (reference type)

* 객체, 배열, 함수 ...
* Object 형식의 타입

참조 타입의 변수는 실제 데이터가 저장된 주소를 참조한다.

```javascript
let arr = [];
let copyarr = arr;

// arr와 copyarr은 동일한 주소값을 참조한다.
```

## 출처

* [꿀로그 | 2021.06.24 | 리액트 불변성이란 무엇이고, 왜 지켜야 할까?](https://hsp0418.tistory.com/171)
* [지속가능한 개발 블로그 | 2021.03.16 | 자바스크립트에서 불변성(Immutability)이란](https://sustainable-dev.tistory.com/156)
* [박해씨의 기묘한 프론트엔드 | 2020년 9월 16일 | \[Java Script\] 원시타입과 참조타입](https://velog.io/@nomadhash/Java-Script-%EA%B9%8A%EC%9D%80-%EB%B3%B5%EC%82%AC%EC%99%80-%EC%96%95%EC%9D%80-%EB%B3%B5%EC%82%AC)

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

## 불변성을 지키는 방법

* spread operator, map, filter, slice, reduce 등등 새로운 배열을 반환하는 메소드들을 활용
* splice는 원본데이터를 변경함
*   setState를 이용할 때 원시타입 경우에는 값을 바로 넣어주어도 되지만

    참조타입인 경우에는 새로운 객체나 배열을 생성한 후 값을 넣어주어야 함

```javascript
// 원시타입
const [str, setStr] = useState('test')
setState('test2')

// 참조타입
const [person, setPerson] = useState({ name: '', age: 10 })
setState({...person, name: '홍길동'})
```

## 불변성을 지키는 중요한 이유

### 사이드 이펙트 방지 및 프로그래밍 구조의 단순성

* 사용할 데이터가 어디서 어떻게 바뀌어가는지 흐름을 쫓아가기 어려움
* 예기치 못한 side effects나 버그로 이어지게 만듬
* 프로그래밍의 복잡도도 올라감

### React에서 최적화 가능

* 리액트에서 setState를 통해 상태값을 변경할 때 얕은 비교를 사용
* 얕은 비교는 객체의 프로퍼티를 하나하나 다 비교하지 않고, 객체의 참조 주소값만 변경되었는지 확인함.
* 얕은 비교는 계산 리소스를 줄여주기 때문에 리액트는 효율적으로 상태를 업데이트 할 수 있음

## 출처

* [꿀로그 | 2021.06.24 | 리액트 불변성이란 무엇이고, 왜 지켜야 할까?](https://hsp0418.tistory.com/171)
* [지속가능한 개발 블로그 | 2021.03.16 | 자바스크립트에서 불변성(Immutability)이란](https://sustainable-dev.tistory.com/156)
* [박해씨의 기묘한 프론트엔드 | 2020년 9월 16일 | \[Java Script\] 원시타입과 참조타입](https://velog.io/@nomadhash/Java-Script-%EA%B9%8A%EC%9D%80-%EB%B3%B5%EC%82%AC%EC%99%80-%EC%96%95%EC%9D%80-%EB%B3%B5%EC%82%AC)

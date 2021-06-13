# 쿠키, 웹 스토리지

## 쿠키 \(Cookie\)

* key, value 데이터 파일로 이름, 값, 만료 날짜\(저장 날짜\), 경로 정보가 필요
* 클라이언트의 브라우저 메모리 혹은 하드디스크에 저장



* 매번 서버에 전송
* 4KB까지의 데이터를 저장할 수 있음
* 유효 기간이 존재
* SameSite 옵션이 Strict가 아닌 경우, 다른 도메인에서 요청할 때도 자동 전송되는 위험성이 있음 \(CSRF 취약\)

## 웹 스토리지 \(Web Storage\)

* 클라이언트에 데이터를 저장할 수 있도록 HTML5부터 새롭게 지원하는 저장소
* key, value로 이루어진 데이터 파일
* 쿠키와 달리, 필요한 경우에만 꺼내 쓰는 것이므로 자동 전송의 위험성이 없음. 다른 도메인에서 요청하는 경우에는, 꺼내 쓰고 싶어도 도메인 단위로 접근이 제한되는 특성 덕분에 값을 꺼내 쓸 수 없음. \(CSRF 안전\)
* 기기마다 차이는 있으나 모바일 2.5MB, 데스크탑 5MB~10MB정도 저장 가능



* 유효 기간이 존재하지 않음
* HTML5를 지원하지 않는 브라우저에서는 사용할 수 없음
* 로컬 스토리지\(Local Storage\), 세션 스토리지\(Session Storage\)

### 로컬 스토리지 \(Local Storage\)

* window.localStorage 객체
* 브라우저를 종료해도 유지되는 데이터로, 명시적으로 지우지 않는 한 영구적으로 저장
* 도메인별로 생성되며, 다른 도메인의 로컬 스토리지에는 접근이 불가능
* 서로 다른 브라우저 탭이라도 동일한 도메인이라면 동일한 로컬 스토리지를 사용

```javascript
window.localStorage.setItem('key','value');
window.localStorage.getItem('key');
window.localStorage.removeItem('key');
window.localStorage.clear(); // All clear
```

### 세션 스토리지 \(Session Storage\)

* window.sessionStorage 객체
* 탭/윈도우 단위로 세션 스토리지가 생성
* window 객체와 동일한 유효 범위 및 생존 기간을 가지며, 탭/윈도우를 닫을 시 데이터가 삭제
* 서로 다른 세션 스토리지는 서로 영향을 주지 않으며 독립적으로 동작
* 윈도우 복제로 생성된 경우, 혹은 스크립트로 새 창을 연 경우 세션 스토리지가 복제되어 생성

```javascript
window.sessionStorage.setItem('key', 'value);
window.sessionStorage.getItem('key');
window.sessionStorage.removeItem('key');
window.sessionStorage.clear(); // All clear
```

## 출처

* [피그브라더 \| 2020. 8. 4. 11:08 \| \[Web\] 쿠키, 웹 스토리지 \(로컬 스토리지, 세션 스토리지\)](https://it-eldorado.tistory.com/90)
* [okayoon 스어네 \| 2019. 6. 5. 10:11 \| 브라우저 쿠키\(Cookie\), 세션스토리지\(Session Storage\), 로컬스토리지\(Local Storage\)](https://okayoon.tistory.com/entry/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80-%EC%BF%A0%ED%82%A4Cookie-%EC%84%B8%EC%85%98%EC%8A%A4%ED%86%A0%EB%A6%AC%EC%A7%80Session-Storage-%EB%A1%9C%EC%BB%AC%EC%8A%A4%ED%86%A0%EB%A6%AC%EC%A7%80Local-Storage)




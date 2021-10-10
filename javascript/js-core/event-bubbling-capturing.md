# 이벤트 전달 방식

## Event Bubbling

해당 이벤트가 더 상위의 화면 요소들로 전달되어 가는 특성

## Event Capturing

해당 이벤트가 하위 요소들로 전달되어 가는 특성

## Event Delegation

* 이벤트 버블링과 캡쳐링을 이용한 방법
* 이벤트 리스너를 해당 요소에 추가하는 대신 그 상위 요소에 추가하여 위임하는 것을 의미
* 요소가 동적으로 추가될 때 이벤트 리스너가 붙지 못하는 문제를 막아주고, 이벤트 리스너의 남발로 인한 메모리 낭비를 줄일 수 있음

## e.preventDefault() vs e.stopPropagation()

### e.preventDefault()

브라우저 고유 동작을 중단시켜줌

* \<a> 태그 href attribute : \<a> 태그 클릭 시 href에 등록된 주소로 이동하지 않도록 막을 수 있음
* \<form> 태그 onSubmit : 페이지가 리프레쉬 되는 고유의 브라우저 동작 막을 수 있음 

### e.stopPropagation()

부모 엘리먼트에게 이벤트 전달을 중단해야 할 때 쓰이는 함수

## 참고

* [캡틴판교 | 이벤트 버블링, 이벤트 캡처 그리고 이벤트 위임까지](https://joshua1988.github.io/web-development/javascript/event-propagation-delegation/)
* [yiyb0603 | 2021년 1월 31일 | \[JS\] e.preventDefault()와 e.stopPropagation()의 차이점](https://velog.io/@yiyb0603/JS-e.preventDefault%EC%99%80-e.stopPropagation%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90)

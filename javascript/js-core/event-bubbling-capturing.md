# 이벤트 전달 방식

## Event Bubbling

해당 이벤트가 더 상위의 화면 요소들로 전달되어 가는 특성

## Event Capturing

해당 이벤트가 하위 요소들로 전달되어 가는 특성

## Event Delegation

* 이벤트 버블링과 캡쳐링을 이용한 방법
* 이벤트 리스너를 해당 요소에 추가하는 대신 그 상위 요소에 추가하여 위임하는 것을 의미
* 요소가 동적으로 추가될 때 이벤트 리스너가 붙지 못하는 문제를 막아주고, 이벤트 리스너의 남발로 인한 메모리 낭비를 줄일 수 있음

## 참고

* [캡틴판교 \| 이벤트 버블링, 이벤트 캡처 그리고 이벤트 위임까지](https://joshua1988.github.io/web-development/javascript/event-propagation-delegation/)


# Location 객체

## Location

* Location 객는 객체가 연결된 장소(URL)을 표현
* `Document.location`와 `Window.location`으로 접근 가능
* document.location보다 window.location으로 접근하는것을 권장

![](<../.gitbook/assets/image (29).png>)

## Properties와 Methods

예제 : http://localhost:8080/test?id=1#abc

![](<../.gitbook/assets/image (30).png>)

### properties

| property | description          | example                             |
| -------- | -------------------- | ----------------------------------- |
| hash     | 주소값에 붙어있는 anchor값 반환 | #abc                                |
| host     | URL의 도메인과 포트 반환      | localhost:8080                      |
| hostname | URL의 도메인 반환          | localhost                           |
| href     | URL 반환               | http://localhost:8080/test?id=1#abc |
| orgin    | 프로토콜 + URL의 도메인 + 포트 | http://localhost:8080               |
| pathname | URL 경로 반환            | /test                               |
| port     | 서버 포트 반환             | 8080                                |
| protocol | 프로토콜 반환              | http:                               |
| search   | URL에 붙은 매개변수 반환      | ?id=1                               |

### methods

| method           | description                                                                        |
| ---------------- | ---------------------------------------------------------------------------------- |
| assign(url)      | 주어진 URL의 리소스를 불러옴                                                                  |
| reload(forceget) | <p>현재 URL의 리소스를 다시 불러옴<br>선택적으로 매개변수에 true를 제공해 브라우저 캐시를 무시하고 서버에서 새로 불러올 수 있음</p> |
| replace(url)     | <p>새로운 주소 이동<br>(assign과 다른점은 세션 히스토리가 남지 않기 때문에 back버튼으로 이동 불가) </p><p></p>     |
| toString()       | URL 전체 URL을 String으로 반환                                                            |

## 출처

* [MDN Web Docs > Location](https://developer.mozilla.org/ko/docs/Web/API/Location)
* [양은냄비 | 2016. 10. 22. 01:22 | Location 객체](https://iamawebdeveloper.tistory.com/41)

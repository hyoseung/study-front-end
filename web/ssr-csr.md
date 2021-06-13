# SSR, CSR

## SSR \(Server Side Rendering\)

완전하게 만들어진 HTML 파일을 서버로부터 받아오고 이를 웹브라우저에 렌더링

### 장점

* 초기 로딩속도 빠름
* SEO\(검색엔진 최적화\) 가능

### 단점

* 웹서버에 요청을 할 때마다 브라우저 새로고침이 일어나고 새로운 페이지는 서버에 요청
* 서버에 매번 요청을 하기 때문에 트래픽, 서버 부하가 커짐

## CSR \(Client Side Rendering\)

처음에 웹서버에 요청할 때 데이터가 없는 문서를 반환 -&gt; HTML 및 static 파일들이 로드되면서 데이터가 있으면 데이터를 서버에 요청하고 화면에 렌더링

### 장점

* 사용자 요청이 올 때마다 서버에 리소스를 요청하고 이를 가져와 웹 브라우저에 보여주는 방식
* 서버에 요청하는 횟수가 훨씬 적기 때문에 서버 부담이 덜
* 첫 로딩 이후에는 필요한 부분만 요청하기 때문에 빠르게 Rendering 할 수 있

### 단점

* SEO\(검색엔진 최적화\) 문제가 발생
* 초기 구동속도 느림

![](../.gitbook/assets/image%20%284%29.png)

## 참고

* [https://velog.io/@namezin/CSR-SSR](https://velog.io/@namezin/CSR-SSR)

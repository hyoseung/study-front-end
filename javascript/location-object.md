# Location 객체

## Location

* Location 객는 객체가 연결된 장소\(URL\)을 표현
* `Document.location`와 `Window.location`으로 접근 가능
* document.location보다 window.location으로 접근하는것을 권장

![](../.gitbook/assets/image%20%287%29.png)

## Properties와 Methods

예제 : http://localhost:8080/test?id=1\#abc

![](../.gitbook/assets/image%20%286%29.png)

### properties

| property | description | example |
| :--- | :--- | :--- |
| hash | 주소값에 붙어있는 anchor값 반환 | \#abc |
| host | URL의 도메인과 포트 반환 | localhost:8080 |
| hostname | URL의 도메인 반환 | localhost |
| href | URL 반환 | http://localhost:8080/test?id=1\#abc |
| orgin | 프로토콜 + URL의 도메인 + 포트 | http://localhost:8080 |
| pathname | URL 경로 반환 | /test |
| port | 서버 포트 반환 | 8080 |
| protocol | 프로토콜 반환 | http: |
| search | URL에 붙은 매개변수 반환 | ?id=1 |

### methods

<table>
  <thead>
    <tr>
      <th style="text-align:left">method</th>
      <th style="text-align:left">description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">assign(url)</td>
      <td style="text-align:left">&#xC8FC;&#xC5B4;&#xC9C4; URL&#xC758; &#xB9AC;&#xC18C;&#xC2A4;&#xB97C;
        &#xBD88;&#xB7EC;&#xC634;</td>
    </tr>
    <tr>
      <td style="text-align:left">reload(forceget)</td>
      <td style="text-align:left">&#xD604;&#xC7AC; URL&#xC758; &#xB9AC;&#xC18C;&#xC2A4;&#xB97C; &#xB2E4;&#xC2DC;
        &#xBD88;&#xB7EC;&#xC634;
        <br />&#xC120;&#xD0DD;&#xC801;&#xC73C;&#xB85C; &#xB9E4;&#xAC1C;&#xBCC0;&#xC218;&#xC5D0;
        true&#xB97C; &#xC81C;&#xACF5;&#xD574; &#xBE0C;&#xB77C;&#xC6B0;&#xC800;
        &#xCE90;&#xC2DC;&#xB97C; &#xBB34;&#xC2DC;&#xD558;&#xACE0; &#xC11C;&#xBC84;&#xC5D0;&#xC11C;
        &#xC0C8;&#xB85C; &#xBD88;&#xB7EC;&#xC62C; &#xC218; &#xC788;&#xC74C;</td>
    </tr>
    <tr>
      <td style="text-align:left">replace(url)</td>
      <td style="text-align:left">
        <p>&#xC0C8;&#xB85C;&#xC6B4; &#xC8FC;&#xC18C; &#xC774;&#xB3D9;
          <br />(assign&#xACFC; &#xB2E4;&#xB978;&#xC810;&#xC740; &#xC138;&#xC158; &#xD788;&#xC2A4;&#xD1A0;&#xB9AC;&#xAC00;
          &#xB0A8;&#xC9C0; &#xC54A;&#xAE30; &#xB54C;&#xBB38;&#xC5D0; back&#xBC84;&#xD2BC;&#xC73C;&#xB85C;
          &#xC774;&#xB3D9; &#xBD88;&#xAC00;)
          <br />
        </p>
        <p>
          <br />
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">toString()</td>
      <td style="text-align:left">URL &#xC804;&#xCCB4; URL&#xC744; String&#xC73C;&#xB85C; &#xBC18;&#xD658;</td>
    </tr>
  </tbody>
</table>

## 출처

* [MDN Web Docs &gt; Location](https://developer.mozilla.org/ko/docs/Web/API/Location)
* [양은냄비 \| 2016. 10. 22. 01:22 \| Location 객체](https://iamawebdeveloper.tistory.com/41)


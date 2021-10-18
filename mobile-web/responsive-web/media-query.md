# 미디어 쿼리

## 미디어 쿼리란?

* 미디어에게 질문하고 감지하여 웹사이트를 변경하는 기술
* 컴퓨터나 기기의 환경 또는 종류를 감지해야 그 기기에 맞게 웹 사이트의 구조를 바꿀수 있음

> @media \[only 또는 not] \[미디어 유형] \[and 또는 ,] (조건문) {실행문}

![](<../../.gitbook/assets/image (44) (1) (1).png>)

```css
HTML과 CSS 파일을 별도로 관리하므로 불러오는 속도도 빠르고, 관리면에서도 효율적

<link rel="stylesheet" href="xxx.css">
```

{% hint style="info" %}
* 대소문자 구별안함
* IE 6,7,8 버전에서는 미디어 쿼리 지원 안함
{% endhint %}

## 미디어 쿼리 문법

### @media

미디어 쿼리 문법의 시작

### \[only 또는 not]

* only : 미디어 쿼리를 지원하는 브라우저에서만 미디어 쿼리를 해석하게 해주는 키워드
* not : not 다음에 오는 조건을 부정하는 키워드

### 미디어 유형

| 기기명                         | 설명                             |
| --------------------------- | ------------------------------ |
| all                         | 모든장치, 기본값                      |
| screen                      | 컴퓨터 화면 or 스마트 기기 화면            |
| tv                          | 영상과 음성이 동시에 출력되는 장치            |
| print, projection, handheld | 인쇄, 프로젝터, 소형 장치                |
| speech, aural               | 음성 출력, 음성 합성(화면을 읽어 소리로 출력) 장치 |
| embossed, braille           | 점자 인쇄 장치, 점자 표시 장치             |
| tty                         | 디스플레이 기능이 제한된 장치               |

### \[and 또는 , 콤마]

> @media A and B{실행문}
>
> @media A, B{실행문}

### (조건문)

and나 콤마를 이용하여 두가지 이상 작성할 수 있음. 생략도 가능

![](<../../.gitbook/assets/image (45).png>)

* 각각의 해상도 사이즈 알기 :  [https://css-tricks.com/snippets/css/media-queries-for-standard-devices/](https://css-tricks.com/snippets/css/media-queries-for-standard-devices/)
* 기기별 쉽게 보기 : [http://nmsdvid.com/snippets/](http://nmsdvid.com/snippets/)

### {실행문}

css 코드 작성

> @media {실행문}

## 출처

* Do it! 반응형 웹 페이지 만들기 | 김운아 | 이지스퍼블리싱
* [강인규 블로그 | 2017-12-06 | 미디어 쿼리 (Media Queries)](https://innks.github.io/2017/12/06/css/Media-Queries/)

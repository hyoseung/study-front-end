# 가변그리드

## 가변 그리드란?

* Fluid Layout, Flexible Layout, Flexible Grid 등 다양하게 부르지만 의미는 모두 동일
* 화면의 크기에 관계없이 자유롭게 늘어나거나 줄어들 수 있도록 픽셀(px) 대신 퍼센트(%)로 제작하는 기술

## 가변 그리드 공식

> (가변 크기로 만들 박스의 가로 너비 / 가변 크기로 만들 박스를 감싸고 있는 박스의 가로 너비) \* 100 = 가변 크기의 % 값

## 가변 마진과 가변 패딩

### 가변 마진

> (가변 마진을 적용할 마진값 / 적용할 박스를 감싸고 있는 박스의 가로 너비) \* 100 = 가변 마진

![](<../../.gitbook/assets/image (31).png>)

```css
<style>
#wrap {
  width: 90%;
  margin: 0 auto;
}

#wrap div {
  display: inline-block;
  width: 31.25%; /* 300/960 * 100 */
  ...
}

#wrap div:first-child {
  margin-right: 37.5%; /* 360/960 * 100 */
  ...
}
</style>

<div id="wrap">
<div></div><div></div>
</div>
```

{% hint style="info" %}
display 속성

* inline: 줄바꿈X, 한줄에 나란히 배치, widht/height 무시, margin/padding 좌우O, 상하X
* block: 줄바꿈O, width/height/margin/padding 모두 반영
* inline-block: 줄바꿈X, width/height/margin/padding 모두 반영
{% endhint %}

### 가변 패딩

가변 패딩은 가변 마진과 달리 박스 width에 포함되어 있음

> (가변 패딩을 적용한 패딩값 / 적용할 박스를 감싸고 있는 박스의 가로 너비) \* 100 = 가변 패딩값

#### 기본방법

![](<../../.gitbook/assets/image (32).png>)

```css
<style>
#wrap {
  width: 90%;
  margin: 0 auto;
  ...
}

#wrap p {
  padding: 40px 4.1666%;
  /* 40/960 * 100 */
}
</style>

<div id="wrap">
  <p>...</p>
</div>
```

#### 제한적인 조건

정해진 width값 이상이 되지 말아야하는 경우

![](<../../.gitbook/assets/image (33).png>)

```css
<style>
#wrap {
  width: 90%;
  margin: 0 auto;
  ...
}

#wrap p {
  width: 52.083%;
  /* 500/960 * 100  => 600-(50*2)=500 */
  padding: 50px 5.20833%;
  /* 50/960 * 100 */
}
</style>

<div id="wrap">
  <p>...</p>
</div>
```

### `calc`

가변 마진과 가변 패딩은 브라우저 비율에 따라 마진과 패딩도 줄어드는 문제가 있음. 박스는 가변적이나 마진이나 패딩은 고정되어 있도록 설정하고 싶을 때 `calc` 함수 사용

박스에 margin을 50px 고정하고 싶을 경우

```css
<style>
#wrap {
  width: 90%;
  margin: 0 auto;
}

#wrap div {
  width: calc(100% - 100px); /* 50*2=100 */
  margin: 50px;
}
</style>

<div id="wrap">
  <div></div>
</div>
```

## 가변 폰트

### em

웹 페이지를 표시하는 모니터 해상도에 따라 픽셀 크기가 달라지기 때문에 상대적인 단위인 em을 사용하는 것이 좋음

em단위는 대문자 M의 너비를 1em으로 표현한 것으로, 16px = 1em

[PXtoEM 사이트](http://pxtoem.com)

> (가변 폰트를 적용할 글자 크기값 / 적용할 요소를 감싸고 있는 요소의 글자 크기값) = 가변 폰트값

### rem

em 단위는 자신의 부모 박스에 글자 크기가 지정되어 있을 경우 자식 박스에게 글자 크기가 상속됨

rem 단위 웹 문서의 시작인 \<html>\</html> 태그 기준으로 하기 때문에 상속 문제가 발생하지 않음

### vw (viewport width)

* 웹 브라우저 너비를 100을 기준으로하여 크기를 결정
* (vw 단위를 적용할 글자 크기 \* 브라우저의 너비 값) / 100
* ex) 5vw : 5%, 너비가 1280일 경우 (5\*1280)/100 = 64px

### vh (viewport height)

* 웹 브라우저 높이를 100을 기준으로하여 크기를 결정
* (vh 단위를 적용할 글자 크기 \* 브라우저의 높이 값) / 100

### vmin, vmax

* 웹 브라우저의 너비와 높이 중 짧은/큰 쪽을 기준으로 하여 크기를 결정하는 단위

## 가변 이미지와 가변 동영상

```css
<style>
img, video {
  width: 100%;
  max-width: 100%;
}
</style>
```

### 유튜브 같은 멀티미디어

* 16:9 비율로 동영상을 제공 -> 패딩 속성을 이용하여 가변적 요소 만들 수 있음
* fitvids와 같은 라이브러리 사용

```css
<style>
#wrap {
  position: relative;
  padding-bottom: 56.25% /* 9/16 */
  height: 0;
  overflow: hidden;  
}

iframe {
  position: absolute;
  top: 0;
  left: 0;
  hegith: 100%
}
</style>
<body>
  <div id="wrap">
    <iframe></iframe>
  </div>
</body>
```

## 출처

* Do it! 반응형 웹 페이지 만들기 | 김운아 | 이지스퍼블리싱

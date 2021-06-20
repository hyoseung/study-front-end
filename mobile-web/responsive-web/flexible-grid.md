# 가변그리드

## 가변 그리드란?

* Fluid Layout, Flexible Layout, Flexible Grid 등 다양하게 부르지만 의미는 모두 동일
* 화면의 크기에 관계없이 자유롭게 늘어나거나 줄어들 수 있도록 픽셀\(px\) 대신 퍼센트\(%\)로 제작하는 기술

## 가변 그리드 공식

> \(가변 크기로 만들 박스의 가로 너비 / 가변 크기로 만들 박스를 감싸고 있는 박스의 가로 너비\) \* 100 = 가변 크기의 % 값

## 가변 마진과 가변 패딩

### 가변 마진

#### 공식

> \(가변 마진을 적용할 마진값 / 적용할 박스를 감싸고 있는 박스의 가로 너비\) \* 100 = 가변 마진

![](../../.gitbook/assets/image%20%288%29.png)

```markup
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

### 가변 패딩

가변 패딩은 가변 마진과 달리 박스 width에 포함되어 있음

#### 공식

> \(가변 패딩을 적용한 패딩값 / 적용할 박스를 감싸고 있는 박스의 가로 너비\) \* 100 = 가변 패딩값

#### 공식 - 기본방법

![](../../.gitbook/assets/image%20%2810%29.png)

```markup
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

#### 공식 - 제한적인 조건

정해진 width값 이상이 되지 말아야하는 경우

![](../../.gitbook/assets/image%20%289%29.png)

```markup
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

### calc

가변 마진과 가변 패딩은 브라우저 비율에 따라 마진과 패딩도 줄어드는 문제가 있음. 박스는 가변젹이되 마진이나 패딩은 고정되어 있도록 설정하고 싶을 때 `calc` 함수 사용

박스에 margin을 50px 고정하고 싶을 경우

```markup
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

## 출처

* Do it! 반응형 웹 페이지 만들기 \| 김운아 \| 이지스퍼블리싱


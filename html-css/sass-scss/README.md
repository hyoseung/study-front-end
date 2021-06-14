# Sass \(SCSS\)

## Sass / SCSS

### CSS Preprocessor

* Sass, Less, postCSS, Stylus 등 CSS Preprocessor\(전처리기\)라고 함
* Sass자체로 브라우저에 적용하는 것이 아니라 CSS를 확장해서 쉽고 편리하게 쓰기 위해 쓰는 스크립팅 언어
* Sass로 작성한 코드는 컴파일을 해서 일반 CSS의 문법으로 바꾼 뒤 적용

![https://velog.io/@jch9537/CSS-SCSS-SASS](../../.gitbook/assets/image%20%285%29.png)

### 사용하는 이유

* CSS가 복잡한 언어는 아니지만 작업이 크고 고도화 될수록 복잡해지고, 불편함
* CSS 태생적 한계를 보완하기 위해 유용한 도구들을 제공
  * 변수의 사용
  * 조건문과 반복문
  * Import
  * Nesting
  * Mixin
  * Extend/Inheritance

### Sass와 SCSS 차이

* SCSS는 Sass\(Syntactically Awesome Style Sheets\) 버전 3에서 새롭게 등장
* Sass 버전 3이상부터는 SCSS 사용
* SCSS는 CSS 구문과 완전히 호환되도록 새로운 구문을 도입해 만든 Sass의 모든 기능을 지원하는 CSS의 상위집합\(Superset\)
* SCSS가 더 넓은 범용성과 CSS의 호환성 등의 장점으로 SCSS를 사용하기를 권장하고 있음

### CSS, Sass, SCSS 비교

<table>
  <thead>
    <tr>
      <th style="text-align:left">CSS</th>
      <th style="text-align:left">Sass</th>
      <th style="text-align:left">SCSS</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>.list {
          <br />
        </p>
        <p>width: 100px;
          <br />
        </p>
        <p>float: left;
          <br />
        </p>
        <p>}
          <br />
        </p>
        <p>li {
          <br />
        </p>
        <p>color: red;
          <br />
        </p>
        <p>background: url(&quot;./image.jpg&quot;);
          <br />
        </p>
        <p>}
          <br />
        </p>
        <p>li:last-child {
          <br />
        </p>
        <p>margin-right: -10px;
          <br />
        </p>
        <p>}
          <br />
        </p>
        <p></p>
      </td>
      <td style="text-align:left">
        <p>.list
          <br />
        </p>
        <p>width: 100px
          <br />
        </p>
        <p>float: left
          <br />
        </p>
        <p>li
          <br />
        </p>
        <p>color: red
          <br />
        </p>
        <p>background: url(&quot;./image.jpg&quot;)
          <br />
        </p>
        <p>&amp;:last-child
          <br />
        </p>
        <p>margin-right: -10px</p>
      </td>
      <td style="text-align:left">
        <p>.list {
          <br />
        </p>
        <p>width: 100px;
          <br />
        </p>
        <p>float: left;
          <br />
        </p>
        <p>li {
          <br />
        </p>
        <p>color: red;
          <br />
        </p>
        <p>background: url(&quot;./image.jpg&quot;);
          <br />
        </p>
        <p>&amp;:last-child {
          <br />
        </p>
        <p>margin-right: -10px;
          <br />
        </p>
        <p>}
          <br />
        </p>
        <p>}
          <br />
        </p>
        <p>}</p>
      </td>
    </tr>
  </tbody>
</table>

## Vue에 적용하기

* node-sass : deprecated
* sass \(Dart Sass\)
  * [https://sass-lang.com/dart-sass](https://sass-lang.com/dart-sass)
* sass-loader
  * Loads a Sass/SCSS file and compiles it to CSS
  * [https://github.com/webpack-contrib/sass-loader](https://github.com/webpack-contrib/sass-loader)

```bash
yarn add sass sass-loader
npm install --save sass sass-loader
```

### local에 SCSS 적용

```markup
<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <router-view/>
</template>

<style lang="scss">
#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;
  }
  a.router-link-exact-active {
    color: #42b983;
  }
}
</style>
```

### .scss 파일 import

```css
// 경로 : @/assets/common.scss
// common.scss

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;
  }
  a.router-link-exact-active {
    color: #42b983;
  }
}
```

```markup
<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <router-view/>
</template>

<style lang="scss">
import '@/assets/common';

</style>
```

## 출처

* [January \| 2018 \| Sass\(SCSS\) 완전 정복!](https://heropy.blog/2018/01/31/sass/)
* [lannstark \| 2019.07.23. 19:43 \| vue에 SASS 적용하기](https://lannstark.tistory.com/7)
* [jch9537 \| 2020년 4월 9일 \| CSS & SCSS & SASS](https://velog.io/@jch9537/CSS-SCSS-SASS)
* [velopert \| 2016년 6월 6일 \| Sass 강좌 – 한 눈에 보기](https://velopert.com/1712)
* [웹 프로그래밍 튜토리얼 \| 4.1 Sass - Basics](https://poiemaweb.com/sass-basics)
* [ma.ro \| 2019. 6. 11. 15:34 \| SASS\(SCSS\) 시작하기 - VS CODE설치 및 셋팅](https://mahyuna.tistory.com/4)



* sass/scss -&gt; css : [https://www.sassmeister.com/](https://www.sassmeister.com/)


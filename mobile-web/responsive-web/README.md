# 반응형 웹

## 반응형 vs 적응형

### 반응형 웹 \(RWD: Responsive Web Design\)

* 웹의 해상도, 레이아웃 등이 디바이스에 따라 반응하여 유동적으로 변환되는 웹페이지
* 한 가지 웹사이트로 다양한 종류의 기기에 최적화된 화면을 보여주는 것

### 적응형 웹 \(AWD: Adaptive Web Design\)

* 서버 또는 브라우저 기반의 기기 감지 방법을 사용하여 각 기기에 적합한 UI 템플릿을 제공하는 방식
* 선별된 기기 유형에 따라 별도의 독립적인 템플릿이 요구됨
* ex\) 네이버 등의 포털 사이트는 모바일 환경에서 기존 사이트의 주소로 접속할 경우, 이를 감지하여 모바일 전용 페이지로 redirection 한다.

### 비교

<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left">&#xBC18;&#xC751;&#xD615; &#xC6F9;</th>
      <th style="text-align:left">&#xC801;&#xC751;&#xD615;</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">&#xAE30;&#xAE30;&#xAC10;&#xC9C0;</td>
      <td style="text-align:left">&#xBBF8;&#xB514;&#xC5B4;&#xCFFC;&#xB9AC;&#xB85C; &#xAE30;&#xAE30; &#xAC10;&#xC9C0;</td>
      <td
      style="text-align:left">&#xC11C;&#xBC84; &#xB610;&#xB294; &#xBE0C;&#xB77C;&#xC6B0;&#xC800;&#xC5D0;&#xC11C;
        &#xAE30;&#xAE30; &#xAC10;&#xC9C0;</td>
    </tr>
    <tr>
      <td style="text-align:left">&#xCF58;&#xD150;&#xCE20; &#xCD5C;&#xC801;&#xD654;</td>
      <td style="text-align:left">
        <p>&#xBAA8;&#xB4E0; &#xCF58;&#xD150;&#xCE20; &#xB2E4;&#xC6B4;&#xB85C;&#xB4DC;</p>
        <p>&#xAE30;&#xAE30; &#xCD5C;&#xC801;&#xD654;&#xC640; &#xC0C1;&#xAD00;&#xC5C6;&#xC774;
          &#xBAA8;&#xB4E0; &#xCF58;&#xD150;&#xCE20;&#xAC00; &#xB2E4;&#xC6B4;&#xB85C;&#xB4DC;
          &#xB418;&#xC9C0;&#xB9CC;, &#xC77C;&#xBD80; &#xCF58;&#xD150;&#xCE20;&#xB9CC;
          &#xC0AC;&#xC6A9;&#xB418;&#xB294; &#xBC29;&#xC2DD;</p>
      </td>
      <td style="text-align:left">
        <p>&#xD544;&#xC694;&#xD55C; &#xCF58;&#xD150;&#xCE20;&#xB9CC; &#xB2E4;&#xC6B4;&#xB85C;&#xB4DC;</p>
        <p>&#xAC10;&#xC9C0;&#xB41C; &#xAE30;&#xAE30;&#xC5D0; &#xCD5C;&#xC801;&#xD654;&#xB41C;
          &#xB9AC;&#xC18C;&#xC2A4;&#xB9CC; &#xB2E4;&#xC6B4;&#xB85C;&#xB4DC; &#xBC1B;&#xC544;
          &#xC0AC;&#xC6A9;</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xAE30;&#xAE30; &#xD2B9;&#xC131;&#xBCC4;
        <br />&#xCC98;&#xB9AC;&#xBC29;&#xBC95;</td>
      <td style="text-align:left">
        <p>&#xD558;&#xB098;&#xC758; &#xD15C;&#xD50C;&#xB9BF;</p>
        <p>&#xD558;&#xB098;&#xC758; &#xD15C;&#xD50C;&#xB9BF;&#xC774; &#xAE30;&#xAE30;&#xC5D0;
          &#xC0C1;&#xAD00;&#xC5C6;&#xC774; &#xC801;&#xC6A9;&#xB41C;&#xB2E4;. &#xC0AC;&#xC774;&#xD2B8;
          &#xB3D9;&#xC791;&#xC740; &#xBCC4;&#xB3C4; &#xAC10;&#xC9C0;&#xC5D0; &#xB530;&#xB978;
          &#xBCC0;&#xACBD;&#xC774; &#xC544;&#xB2D0; &#xACBD;&#xC6B0; &#xB3D9;&#xC77C;&#xD558;&#xAC8C;
          &#xC801;&#xC6A9; &#xB41C;&#xB2E4;.</p>
      </td>
      <td style="text-align:left">
        <p>&#xAE30;&#xAE30; &#xB9C8;&#xB2E4; &#xB2E4;&#xB978; &#xD15C;&#xD50C;&#xB9BF;</p>
        <p>&#xC900;&#xBE44;&#xB41C; &#xD15C;&#xB9BF;&#xC774; &#xAE30;&#xAE30;&#xC5D0;
          &#xB530;&#xB77C; &#xB2E4;&#xB974;&#xAC8C; &#xC801;&#xC6A9;&#xB41C;&#xB2E4;.
          &#xC0AC;&#xC774;&#xD2B8; &#xB3D9;&#xC791;&#xC740; &#xAE30;&#xAE30; &#xC720;&#xD615;&#xC5D0;
          &#xB530;&#xB77C; &#xBCC0;&#xACBD;&#xB41C;&#xB2E4;.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xB85C;&#xB4DC; &#xC18D;&#xB3C4;</td>
      <td style="text-align:left">
        <p>&#xB290;&#xB9BC;</p>
        <p>&#xAE30;&#xAE30;&#xC5D0; &#xC0C1;&#xAD00;&#xC5C6;&#xC774; &#xBAA8;&#xB4E0;
          &#xB9AC;&#xC18C;&#xC2A4;&#xB97C; &#xB2E4;&#xC6B4;&#xBC1B;&#xC544; &#xC0AC;&#xC6A9;&#xD558;&#xAE30;
          &#xB54C;&#xBB38;&#xC5D0; &#xB85C;&#xB4DC; &#xC18D;&#xB3C4;&#xAC00; &#xB290;&#xB9AC;&#xB2E4;.</p>
      </td>
      <td style="text-align:left">
        <p>&#xBE60;&#xB984;</p>
        <p>&#xAC01; &#xAE30;&#xAE30;&#xC5D0; &#xD544;&#xC694;&#xD55C; &#xB9AC;&#xC18C;&#xC2A4;&#xB9CC;
          &#xB2E4;&#xC6B4;&#xB85C;&#xB4DC; &#xBC1B;&#xC544; &#xC0AC;&#xC6A9;&#xD558;&#xAE30;
          &#xB54C;&#xBB38;&#xC5D0; &#xB85C;&#xB4DC; &#xC18D;&#xB3C4;&#xAC00; &#xBE60;&#xB974;&#xB2E4;.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">&#xAC1C;&#xBC1C;/&#xBC30;&#xD3EC;</td>
      <td style="text-align:left">
        <p>&#xAE30;&#xC874; &#xC0AC;&#xC774;&#xD2B8;&#xB97C; &#xC804;&#xBA74; &#xB9AC;&#xB274;&#xC5BC;
          &#xD558;&#xC5EC; &#xAC1C;&#xBC1C;</p>
        <p>&#xAE30;&#xC874; &#xC0AC;&#xC774;&#xD2B8;&#xB97C; &#xC804;&#xBA74; &#xC7AC;&#xAC1C;&#xBC1C;
          &#xD574;&#xC57C;&#xD55C;&#xB2E4;. &#xBAA8;&#xB4E0; &#xAE30;&#xAE30;&#xC5D0;&#xC11C;&#xC758;
          &#xC0AC;&#xC6A9;&#xC790; &#xC778;&#xD130;&#xB809;&#xC158;&#xC744; &#xAE30;&#xD68D;/&#xB514;&#xC790;&#xC778;
          &#xB2E8;&#xACC4;&#xC5D0;&#xC11C;&#xBD80;&#xD130; &#xBA74;&#xBC00;&#xD558;&#xAC8C;
          &#xAC80;&#xD1A0;&#xD558;&#xACE0; &#xACE0;&#xB824;&#xD574;&#xC57C;&#xD55C;&#xB2E4;.</p>
      </td>
      <td style="text-align:left">
        <p>&#xAE30;&#xC874; &#xC0AC;&#xC774;&#xD2B8; &#xBCC0;&#xACBD;&#xC5C6;&#xC774;
          &#xAC1C;&#xBC1C; &#xAC00;&#xB2A5;&#xD558;&#xC9C0;&#xB9CC; &#xCD94;&#xAC00;
          &#xBE44;&#xC6A9; &#xBC1C;&#xC0DD;</p>
        <p></p>
      </td>
    </tr>
  </tbody>
</table>

## 출처

* [캐스팅엔 IT 매니저   \| 2020-08-18 \| 반응형 웹과 모바일 웹, 어떻게 개발할까요](https://www.castingn.com/sourcing/kkultip_detail/113)
* [phrygia   \| 2020-11-10 \| \[web\] 반응형\(RWD\)웹과 적응형\(AWD\)웹](https://phrygia.github.io/2020-11-10/rwd-awd)


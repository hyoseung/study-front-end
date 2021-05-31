# 브라우저 동작원리

## 동작 원리

![&#xC911;&#xC694; &#xB80C;&#xB354;&#xB9C1; &#xACBD;&#xB85C;\(Critical Rendering Path\)](https://lh6.googleusercontent.com/D3ySuowu9dZxfmBZSb4wjUb-tu_hChhuz_TJmQUVscKbN9ne3va-wqSOg4ZYQ_uf4SeJwxb7JLSzGYT4le6kPxEXSn5LQTUq_WUQAaVAxnoBtznoGuwkwzLGnNGLDa5SMU1lV_RT)

1. HTML을 파싱한다.
2. HTML 파싱 결과로 DOM tree를 생성한다.
3. 파싱 중 CSS 링크를 만나면 CSS 파일을 요청해 받아온다.
4. CSS 파일을 파싱해 CSSOM\(CSS Object Model\) tree를 생성한다.
5. DOM과 CSSOM을 결합하면 Render tree를 생성한다. Render tree에는 페이지를 렌더링 하는데 필요한 노드만 포함한다. \(display: none 과 head태그 제외\)
6.  Render tree 기반으로 각각의 화면의 어디에 위치할 것인지 그린다.
7. 픽셀을 화면에 paint 한다.

### &lt;script&gt; 태그를 만날 경우

자바스크립트는 렌더링 엔진이 아닌 자바스크립트 엔진이 처리한다. HTML 파서는 &lt;script&gt; 태그를 만나면 자바스크립트 코드를 실행하기 위해 DOM 생성 프로세스를 중지하고 자바스크립트 엔진으로 제어 권한을 넘긴다. 제어 권한을 넘겨 받은 자바스크립트 엔진은 &lt;script&gt; 태그 내의 자바스크립트 코드 또는 &lt;script&gt; 태그의 src 어트리뷰트에 정의된 자바스크립트 파일을 로드하고 파싱하여 실행한다. 자바스크립트의 실행이 완료되면 다시 HTML 파서로 제어 권한을 넘겨서 브라우저가 중지했던 시점부터 DOM 생성을 재개한다.

동기적으로 HTML, CSS, Script를 처리하기 때문에 보통 &lt;script&gt; 태그는 body 요소의 가장 아래에 두거나, &lt;script&gt; 태그에 async 속성을 부여하는 것이 좋다.

### 추가된 개념

![](https://lh4.googleusercontent.com/rOC3Dma28FJMLOEVaThNeUc8aAl3S1U-TFBUgfCGYBdJNrgbRolh2mv5D0CEhBM30y_voFie6RH9-BrVmuczpPyxtXujqHsClYs_SvoLuJH0m5LnIYcCNi1ZuS3vM63gT8ehEPx-)

#### Update Layer Tree

* 렌더링에 사용될 최종 Layer들을 계산해서 생성하는 과정.
* Layer 로 분리해서 합치는 방식으로 렌더링한다.
* Layer 는 빠르지만 메모리를 많이 사용한다.

#### Composite

* 레이어들을 합성하여 한장의 Bitmap으로 만드는 과정 \(이후 하나의 페이지를 생성\)
* paint 는 Layer 별로 paint하며, Tiled backing store 기법을 사용함.

## **Reflow와 Repainting**

### **reflow**

이벤트에 따라 html 요소의 크기나 위치등 레이아웃 수치를 수정하면 그에 영향을 받는 자식 노드나 부모 노드들을 포함하여 Layout 과정을 다시 수행하게 된다. 이렇게 되면 Render Tree와 각 요소들의 크기와 위치를 다시 계산하게 되는데 이러한 과정을 Reflow라고 한다.

#### reflow가 일어나는 경우

* 페이지 초기 렌더링 시\(최초 Layout 과정\)
* 윈도우 리사이즈 시 \(Viewport 크기 변경시\)
* 노드 추가 또는 제거
* 요소의 위치, 크기 변경 \(left, top, margin, padding, border, width, height, 등..\)
* 폰트 변경 과\(텍스트 내용\) 이미지 크기 변경\(크기가 다른 이미지로 변경 시\)  ****

### repainting

Reflow만 수행되면 실제 화면에 반영되지 않는다. 위에서 언급된 렌더링 과정과 같이 Render Tree를 다시 화면에 그려주는 과정이 필요하다. Paint 단계가 다시 수행되는 것이며 이를 Repaint 라고 합니다.

background-color, visibility와 같이 레이아웃에는 영향을 주지 않는 스타일 속성이 변경되었을 때는 Reflow를 수행할 필요가 없기 때문에 Repaint만 수행한다.

## **visibility vs hidden**

| visibility: hidden | display: none |
| :--- | :--- |
| 요소를 보이지 않게 만들지만, 이 요소는 여전히 레이아웃에서 공간을 차지한다. | 요소가 보이지 않으며 레이아웃에 포함되지도 않도록 렌더링 트리에서 요소를 완전히 제거한다. |

## 참고

* [https://developers.google.com/web/updates/2018/09/inside-browser-part3?hl=ko](https://developers.google.com/web/updates/2018/09/inside-browser-part3?hl=ko)
* [https://mingcoder.me/2020/02/25/Programming/Basic/browser-process/](https://mingcoder.me/2020/02/25/Programming/Basic/browser-process/)
* [https://boxfoxs.tistory.com/408](https://boxfoxs.tistory.com/408)




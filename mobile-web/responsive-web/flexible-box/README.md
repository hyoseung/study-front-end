# 플렉서블 박스

## 플렉서블 박스란?

* 가변적인 박스를 만드는 기술인 동시에 웹사이트의 구조 설계를 위한 새로운 기술
* 가변그리드 기술을 이용해 만드는 가변적인 박스를 간단하게 만들어줄 뿐만 아니라 박스를 손쉽게 배치 할 수 있음

## 플렉서블 박스 기본 개념

### 플렉서블 박스 = 부모 박스

플렉서블 박스에서 부모박스는 가변적인 박스로 작동하기 위한 기본 개념

### 플렉서블 박스의 자식 박스 = 플렉스 아이템

부모박스가 속성값이 적용되어 가변적인 박스로 작동하는 순간부터 플렉서블 박스로 불리듯, 자식박스 역시 속성값에 의해 작동하는 순간부터 플렉스 아이템이라고 불림

### 플렉서블 박스 축

* 주축(Main Axis) : 중심이 되는 축, 주축을 따라 플렉스 아이템이 배치 됨
* 교차축(Cross Axis) : 주축에 교차하는 축

#### 축의 방향

축의 방향은 플렉스 아이템의 배치 방향을 설정하기 위해 사용하는 속상값에 따라 결정됨

#### 축의 시작과 끝

축에 시작과 끝이 존재하는 이유는 플렉스 아이템이 처음 배치되는 위치(시작점)와 플렉스 아이템이 마지막에 배치될 위치(끝점)가 필요하기 때문

![](<../../../.gitbook/assets/image (44) (1).png>)

## 출처

* Do it! 반응형 웹 페이지 만들기 | 김운아 | 이지스퍼블리싱
* [Using U | CSS Flexbox Layout](https://usingu.co.kr/references/css/flexbox-layout/)
* [HEROPY Tech | 2018.09 | CSS Flex(Flexible Box) 완벽가이드](https://heropy.blog/2018/11/24/css-flexible-box/)
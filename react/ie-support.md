# IE 지원

## 설정

### react-scripts 버전 3.2.0으로 다운그레이드

[참고](https://stackoverflow.com/questions/59834690/react-app-polyfill-doesnt-work-in-ie11)

```
yarn add react-scripts@3.2.0
```

&#x20;react-scripts를 3.2.0으로 다운그레이드 할 경우, 아래와 같이 import 필요   &#x20;

```
import React from 'react';
```

### react-app-polyfill 설치

```
// Some code ㅛㅁyarn add react-app-polyfill
```

## 출처

* [고코몽의 프론트엔드 저장소 | 0201.06.18 | React IE 대응](https://msko.tistory.com/63)
* [devyang97 | 2020.08.12 | \[React\] 환경 변수 사용하기 (production/development)](https://velog.io/@devyang97/React-%ED%99%98%EA%B2%BD-%EB%B3%80%EC%88%98-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-productiondevelopment)

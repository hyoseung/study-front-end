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
yarn add react-app-polyfill
```

package.json

```
  "browserslist": {
    "production": [
      ">0.2%",
      "not dead",
      "not op_mini all"
    ],
    "development": [
      "ie 9-10",
      "last 1 chrome version",
      "last 1 firefox version",
      "last 1 safari version"
    ]
  }
```

index.js

* 첫줄에 추가&#x20;

```
import 'react-app-polyfill/ie9'; 
import 'react-app-polyfill/ie11';
import 'react-app-polyfill/stable';
```

## 출처

* [고코몽의 프론트엔드 저장소 | 0201.06.18 | React IE 대응](https://msko.tistory.com/63)
* [devyang97 | 2020.08.12 | \[React\] 환경 변수 사용하기 (production/development)](https://velog.io/@devyang97/React-%ED%99%98%EA%B2%BD-%EB%B3%80%EC%88%98-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-productiondevelopment)

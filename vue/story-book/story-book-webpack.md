# webpack 설정

## @ 경로 설정

`.storybook`에 `main.js` 수정

```javascript
// main.js

const path = require('path');

module.exports = {
  ...
  webpackFinal: async (config, { configType }) => {
    config.resolve.alias = { 
      ...config.resolve.alias,
      "@": path.resolve(__dirname, "../src")
    };

    return config;
  },
}
```

* \_\_dirname : 현재 실행 중인 폴더 경로
* \_\_filename : 현재 실행 중인 파일 경로

## scss 파일 지원

`.storybook`에 `main.js` 수정

```javascript
// main.js

module.exports = {
  ...
  webpackFinal: async (config, { configType }) => {
    config.module.rules.push({
      test: /\.scss$/,
      use: ['style-loader', 'css-loader', 'sass-loader'],
      include: path.resolve(__dirname, '../'),
    });

    return config;
  },
}
```

## 출처

* [캡틴.JS \| 2020. 3. 23. 13:04 \| \[vue.js\] storybook absolute path 설정](https://avengersrhydon1121.tistory.com/276)
* [Storybook 공식 사이 &gt; webpack config 수정](https://storybook.js.org/docs/vue/configure/webpack#extending-storybooks-webpack-config)






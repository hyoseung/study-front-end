# webpack 설정

## @ 경로 설정

`.storybook`에 `main.js` 수정

```javascript
// main.js

const path = require('path');

module.exports = {
  "stories": [
    "../src/**/*.stories.mdx",
    "../src/**/*.stories.@(js|jsx|ts|tsx)"
  ],
  "addons": [
    "@storybook/addon-links",
    "@storybook/addon-essentials"
  ],
  webpackFinal: async (config, { configType }) => {
    // `configType` has a value of 'DEVELOPMENT' or 'PRODUCTION'
    // You can change the configuration based on that.
    // 'PRODUCTION' is used when building the static version of storybook.

    config.resolve.alias = { 
      ...config.resolve.alias,
      "@": path.resolve(__dirname, "../src")
    };

    // Return the altered config
    return config;
  },
}
```

## scss 파일 지원

`.storybook`에 `main.js` 수정

```javascript
// main.js

module.exports = {
  "stories": [
    "../src/**/*.stories.mdx",
    "../src/**/*.stories.@(js|jsx|ts|tsx)"
  ],
  "addons": [
    "@storybook/addon-links",
    "@storybook/addon-essentials"
  ],
  webpackFinal: async (config, { configType }) => {
    // `configType` has a value of 'DEVELOPMENT' or 'PRODUCTION'
    // You can change the configuration based on that.
    // 'PRODUCTION' is used when building the static version of storybook.

    // Make whatever fine-grained changes you need
    config.module.rules.push({
      test: /\.scss$/,
      use: ['style-loader', 'css-loader', 'sass-loader'],
      include: path.resolve(__dirname, '../'),
    });

    // Return the altered config
    return config;
  },
}
```

## 출처

* [캡틴.JS \| 2020. 3. 23. 13:04 \| \[vue.js\] storybook absolute path 설정](https://avengersrhydon1121.tistory.com/276)
* [Storybook 공식 사이 &gt; webpack config 수정](https://storybook.js.org/docs/vue/configure/webpack#extending-storybooks-webpack-config)






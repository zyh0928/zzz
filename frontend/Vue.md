## Installation

### Vue CLI

- vue-cli 全局安装

  ```sh
  yarn global add @vue/cli
  ```

- Create project

  ```sh
  # linux path: /home/<user>/.yarn/bin/vue
  vue create <name>
  ```

- Add `vue.config.js` on root

  ```js
  module.exports = {
    // options...
  };
  ```

- Command

  ```sh
  # 图形化界面
  vue ui

  # 启动热加载，默认端口为 8080
  yarn serve

  # 打包
  yarn build
  ```

### Modules

> dependencies

  ```sh
  yarn add animate.css animejs axios lodash vee-validate vue-i18n vue-router vuetify
  ```

> dev dependencies

  ```sh
  yarn add @types/lodash style-resources-loader -D
  ```

### Icon

- Material Design Icons

  ```html
  <i class="material-icons">icon_name</i>
  ```

  - yarn

    ```sh
    # 安装后导入。不推荐，更新慢
    yarn add material-design-icons
    ```

  - CDN

    ```html
    <link
      href="https://fonts.googleapis.com/icon?family=Material+Icons"
      rel="stylesheet"
    />
    ```

  - **Self Hosting**

    ```css
    /*
      下载字体到本地

      下载 css 文件直接导入

      或在导入的通用样式中添加以下规则
    */
    @font-face {
      font-family: "Material Icons";
      font-style: normal;
      font-weight: 400;
      src: url(https://example.com/MaterialIcons-Regular.woff2) format("woff2");
    }
    .material-icons {
      font-family: "Material Icons", sans-serif;
      font-weight: normal;
      font-style: normal;
      font-size: 24px;
      line-height: 1;
      letter-spacing: normal;
      text-transform: none;
      display: inline-block;
      white-space: nowrap;
      word-wrap: normal;
      direction: ltr;
      font-feature-settings: "liga";
      -webkit-font-feature-settings: "liga";
      -webkit-font-smoothing: antialiased;
      /*
        官方推荐 Size 样式
        &.md-18 { font-size: 18px; }
        &.md-24 { font-size: 24px; }
        &.md-36 { font-size: 36px; }
        &.md-48 { font-size: 48px; }
      */
    }
    ```

## Vue Router

### HTML5 History Mode

默认模式为 hash，URL 会带一个 # 号，history 模式则不带

- Configure router properties

  ```js
  export default new Router({
    mode: 'history',
    routes: [...]
  })
  ```

- Configure NGINX

  ```nginx
  location / {
      root  path/to/root;
      index  index.html  index.htm;
      try_files  $uri  $uri/  /index.html;
  }
  ```

配置通配路由

```js
routes: [
  {
    path: "*",
    name: "NotFound",
    component: () => import("path/to/NotFound")
  }
];
```

## Link

- [**Vue.js**](https://cn.vuejs.org/)

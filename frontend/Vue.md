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
  location <path> {
      try_files $uri $uri/ /index.html;
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

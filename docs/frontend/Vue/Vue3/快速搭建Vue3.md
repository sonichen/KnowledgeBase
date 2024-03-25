## 技术

[Vue3](https://cn.vuejs.org/guide/introduction.html)

[TypeScript](https://www.typescriptlang.org/zh/docs/)

[Vue-Cli脚手架](https://cli.vuejs.org/zh/guide/)

[Arco Design 组件库](https://arco.design/vue/docs/start)

## 环境检查

```
node -v
```

```
npm -v
```

## 初始化

安装脚手架

```
npm install -g @vue/cli
```

检查

```
vue -V
```

## 创建项目

```
vue create 项目名
```

这里 脚手架配置代码美化、自动校验、格式化插件等

```shell
Vue CLI v5.0.8
? Please pick a preset: Manually select features
? Check the features needed for your project: Babel, TS, Router, Vuex, Linter
? Choose a version of Vue.js that you want to start the project with 3.x
? Use class-style component syntax? No
? Use Babel alongside TypeScript (required for modern mode, auto-detected polyfills, transpiling JSX)? Yes
? Use history mode for router? (Requires proper server setup for index fallback in production) Yes
? Pick a linter / formatter config: Prettier
? Pick additional lint features: Lint on save
? Where do you prefer placing config for Babel, ESLint, etc.? In dedicated config files
? Save this as a preset for future projects? No
```

运行

```
npm run serve
```

![image-20240323125316464](assets\image-20240323125316464.png)

## 引入组件

安装依赖

```
npm install --save-dev @arco-design/web-vue
```

配置main.ts

```

// config Component library arco.design
import ArcoVue from "@arco-design/web-vue";
import "@arco-design/web-vue/dist/arco.css";

// Use
createApp(App).use(ArcoVue).use(store).use(router).mount("#app");

```

测试是否引入成功

```
 <a-button type="primary">Primary</a-button>
```

![image-20240323125753753](assets\image-20240323125753753.png)

## 项目布局

全局状态管理

全局权限管理


## 状态管理工具pinia

什么是状态？理解为数据

把共享的数据交给他管理

## 安装

第一步：`npm install pinia`

第二步：操作`src/main.ts

```
import { createApp } from 'vue'
import App from './App.vue'

/* 引入createPinia，用于创建pinia */
import { createPinia } from 'pinia'

/* 创建pinia */
const pinia = createPinia()
const app = createApp(App)

/* 使用插件 */{}
app.use(pinia)
app.mount('#app')
```


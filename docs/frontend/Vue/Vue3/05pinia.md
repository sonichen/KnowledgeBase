## 状态管理工具pinia

什么是状态？理解为数据

有不同组件间进行交互的情况

我们是要考虑把把共享的数据交给他管理

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

/* 使用插件 */
app.use(pinia)
app.mount('#app')
```

![image-20240322152012240](assets\image-20240322152012240.png)



## 案例

### 准备

安装

```
npm i axios
npm i axios
```

准备两个组件

```vue

<template>
    <div class="count">
      <h2>当前求和为：{{ sum }} </h2>
      <!-- // 把值转成数字 -->
      <select v-model.number="n" >
        <!-- // value="1": 默认值是字符串 -->
        <!-- // :value="1"： 默认值是表达式，是数值 -->
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
      </select>
      <button @click="add()">加</button>
      <button @click="minus()" >减</button>
    </div>
  </template>

<script lang="ts">
export default {
    // eslint-disable-next-line vue/multi-word-component-names
    name: 'Count',
}
</script>
<script lang="ts" setup  >
import { ref } from 'vue';
    // 数据
    let sum=ref(1);
    let n=ref(1);
    // 方法
    function add(){
        sum.value+=n.value;
    }
    function minus(){
        sum.value-=n.value;
    }
</script>

<style scoped>
  .count {
    background-color: skyblue;
    padding: 10px;
    border-radius: 10px;
    box-shadow: 0 0 10px;
  }
  select,button {
    margin: 0 5px;
    height: 25px;
  }
</style>
```

```vue
<template>
    <div class="talk">
      <button @click="getLoveTalk">获取一句土味情话</button>
      <ul>
        <li v-for="talk in talkList" :key="talk.id">{{talk.title}}</li>
      </ul>
    </div>
  </template>
<script setup lang="ts" name="LoveTalk">
import {reactive} from 'vue';
import axios from "axios";
import {nanoid} from 'nanoid' // 生成id
// 数据
let talkList = reactive([
  {id:'ftrfasdf01',title:'今天你有点怪，哪里怪？怪好看的！'},
  {id:'ftrfasdf02',title:'草莓、蓝莓、蔓越莓，今天想我了没？'},
  {id:'ftrfasdf03',title:'心里给你留了一块地，我的死心塌地'}
])
// 方法
async function getLoveTalk(){
  // 发请求，下面这行的写法是：连续解构赋值+重命名
  let {data:{content:title}} = await axios.get('https://api.uomg.com/api/rand.qinghua?format=json')
  // 把请求回来的字符串，包装成一个对象
  let obj = {id:nanoid(),title}
  // 放到数组中
  talkList.unshift(obj)
}
</script>

<style scoped>
.talk {
  background-color: orange;
  padding: 10px;
  border-radius: 10px;
  box-shadow: 0 0 10px;
}
</style>
```

App.vue

```vue
<template>
  <div class="app">
    <Count/>
    <LoveTalk/>
  </div>
</template>

<script lang="ts">
import Count from './components/Count.vue';
import LoveTalk from './components/LoveTalk.vue';
 
 
  export default {
    name:'App', //组件名
    components:{Count,LoveTalk} //注册组件
  }
</script>

<style>
  .app {
    background-color: #ddd;
    box-shadow: 0 0 10px;
    border-radius: 10px;
    padding: 20px;
  }
</style>
```

### 读取和存储

![image-20240322152219589](assets\image-20240322152219589.png)

### 配置

src下配置store文件夹（这个相当于pinia的具体体现，落地的东西）

创建和组件文件名对应的ts文件

![image-20240322154143277](assets\image-20240322154143277.png)

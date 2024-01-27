参考文档

[谷歌拓展程序](https://developer.chrome.com/docs/extensions/get-started/tutorial/hello-world?hl=zh-cn)

## Hello World 扩展程序

### 第一个拓展

manifest.json配置文件：描述了扩展程序的功能和配置

action：声明 Chrome 应用作扩展程序的操作图标的图片，以及当用户点击扩展程序的操作图标时在弹出式窗口中显示的 HTML 页面

```
{
    "manifest_version": 3,
    "name": "Hello Extensions",
    "description": "Base Level Extension",
    "version": "1.0",
    "action": {
      "default_popup": "hello.html",
      "default_icon": "hello_extensions.png"
    }
  }
```

hello.html

```
<html>
  <body>
    <h1>Hello Extensions</h1>
  </body>
</html>
```

[hello_extensions.png](https://storage.googleapis.com/web-dev-uploads/image/WlD8wC6g8khYWPJUsQceQkhXSlv1/gmKIT88Ha1z8VBMJFOOH.png)

浏览器配置

谷歌浏览器-->拓展程序，打开开发者模型，选择加载已解压的拓展程序。

注意：manifest_version版本需要在3以上，否则报错和警告。

- Invalid value for 'manifest_version'. Must be an integer either 2 or 3. See developer.chrome.com/extensions/manifestVersion for details.
- **2023 年 1 月**：Chrome 浏览器将[不再运行 Manifest V2 扩展程序](https://developer.chrome.com/blog/mv2-transition?hl=zh-cn)。

图标：https://www.iconfont.cn/

效果

![image-20240105152517769](assets\image-20240105152517769.png)

### 构建扩展程序项目

可以通过多种方式构建扩展程序项目；不过，唯一的前提条件是将 manifest.json 文件放在扩展程序的根目录中，如以下示例所示：

![image-20240105152936001](assets\image-20240105152936001.png)

## 在每个网页上运行脚本

构建一个扩展程序，用于将预期阅读时间添加到任何 Chrome 扩展程序和 Chrome 应用商店文档页面。

## 扩展程序清单

- 它必须位于项目的根目录下。
- 唯一的必需键为 `"manifest_version"`、`"name"` 和 `"version"`。
- 它支持在开发过程中使用注释 (`//`)，但在将代码上传到 Chrome 应用商店之前必须先移除这些注释。

### 提供图标

```
{
  ...
  "icons": {
    "16": "images/icon-16.png",
    "32": "images/icon-32.png",
    "48": "images/icon-48.png",
    "128": "images/icon-128.png"
  }
  ...
}
```

建议使用 PNG 文件

![image-20240106130424579](assets\image-20240106130424579.png)



### 声明内容脚本

扩展程序可以运行用于读取和修改网页内容的脚本。这些脚本称为内容脚本。

```
{
  ...
  "content_scripts": [
    {
      "js": ["scripts/content.js"],
      "matches": [
        "https://developer.chrome.com/docs/extensions/*",
        "https://developer.chrome.com/docs/webstore/*"
      ]
    }
  ]
}
```

### 注入网站

`"matches"` 字段可以有一种或多种[匹配模式](https://developer.chrome.com/docs/extensions/develop/concepts/match-patterns?hl=zh-cn)。这些变量可让浏览器识别要**将内容脚本注入到哪些网站**。匹配模式由三部分组成：`<scheme>://<host><path>`。它们可以包含“`*`”字符。



## 脚本注入当前标签页

### 将扩展 Service Worker 用作事件协调器

扩展程序可以使用[扩展程序的 Service Worker](https://developer.chrome.com/docs/extensions/develop/concepts/service-workers?hl=zh-cn) 在后台监控浏览器事件。Service Worker 是特殊的 JavaScript 环境，用于处理事件，并会在不需要时终止。

首先，在 `manifest.json` 文件中注册 Service Worker：

```
{
  ...
  "background": {
    "service_worker": "background.js"
  },
  ...
}
```



创建一个名为 `background.js` 的文件，并添加以下代码：

```
chrome.runtime.onInstalled.addListener(() => {
  chrome.action.setBadgeText({
    text: "OFF",
  });
});
```

我们的 Service Worker 将监听的第一个事件是 [`runtime.onInstalled()`](https://developer.chrome.com/docs/extensions/reference/api/runtime?hl=zh-cn#event-onInstalled)。此方法可让扩展程序在安装时设置初始状态或完成一些任务。扩展程序可以使用 [Storage API](https://developer.chrome.com/docs/extensions/reference/api/storage?hl=zh-cn) 和 [IndexedDB](https://developer.mozilla.org/docs/Web/API/IndexedDB_API) 存储应用状态。不过，在这种情况下，由于我们只处理两种状态，因此将使用*操作的标记*文本本身来跟踪扩展程序处于“开启”还是“关闭”状态。

### 启用扩展程序操作

```
{
  ...
  "action": {
    "default_icon": {
      "16": "images/icon-16.png",
      "32": "images/icon-32.png",
      "48": "images/icon-48.png",
      "128": "images/icon-128.png"
    }
  },
  ...
}
```

### 通过 `"activeTab"` 权限保护用户隐私

#### 使用 activeTab 权限保护用户隐私

[`activeTab`](https://developer.chrome.com/docs/extensions/reference/manifest/activeTab?hl=zh-cn) 权限授予扩展程序临时性权限，使其能够在当前活跃的标签页上执行代码。它还允许访问当前标签页的[敏感属性](https://developer.chrome.com/docs/extensions/reference/manifest/activeTab?hl=zh-cn#what-activeTab-allows)。

如需使用 `"activeTab"` 权限，请将其添加到清单的权限数组：

```
{
  ...
  "permissions": ["activeTab"],
  ...
}
```

### 跟踪当前标签页的状态

用户点击扩展程序操作后，该扩展程序将检查网址是否与文档页面匹配。接下来，它会检查当前标签页的状态并设置下一个状态。将以下代码添加到 `background.js`：

```
const extensions = 'https://developer.chrome.com/docs/extensions'
const webstore = 'https://developer.chrome.com/docs/webstore'

chrome.action.onClicked.addListener(async (tab) => {
  if (tab.url.startsWith(extensions) || tab.url.startsWith(webstore)) {
    // Retrieve the action badge to check if the extension is 'ON' or 'OFF'
    const prevState = await chrome.action.getBadgeText({ tabId: tab.id });
    // Next state will always be the opposite
    const nextState = prevState === 'ON' ? 'OFF' : 'ON'

    // Set the action badge to the next state
    await chrome.action.setBadgeText({
      tabId: tab.id,
      text: nextState,
    });
...
```

### 添加或移除样式表

```
{
  ...
  "permissions": ["activeTab", "scripting"],
  ...
}
```

background.js


```
  ...
    if (nextState === "ON") {
      // Insert the CSS file when the user turns the extension on
      await chrome.scripting.insertCSS({
        files: ["focus-mode.css"],
        target: { tabId: tab.id },
      });
    } else if (nextState === "OFF") {
      // Remove the CSS file when the user turns the extension off
      await chrome.scripting.removeCSS({
        files: ["focus-mode.css"],
        target: { tabId: tab.id },
      });
    }
  }
});
```





在用户点击扩展程序工具栏图标时运行代码。

使用 [Scripting](https://developer.chrome.com/docs/extensions/reference/api/scripting?hl=zh-cn) API 插入和移除样式表。

使用键盘快捷键执行代码。
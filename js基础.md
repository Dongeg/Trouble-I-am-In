# js 基础语法

## BOM 浏览器对象模型

```js
window.scrollTo(0,1000)  // 页面滚动到指定位置

window.history.length  // 历史页的数量

window.history.back() //上一页

window.history.forward() // 下一页

window.history.go(-1)

// https://cn.vuejs.org/v2/guide/components-custom-events.html#%E8%87%AA%E5%AE%9A%E4%B9%89%E7%BB%84%E4%BB%B6%E7%9A%84-v-model

window.location

hash: "#%E8%87%AA%E5%AE%9A%E4%B9%89%E7%BB%84%E4%BB%B6%E7%9A%84-v-model"  // 锚点
host: "cn.vuejs.org"  //  主机名+端口
hostname: "cn.vuejs.org"  // 主机名
href: "https://cn.vuejs.org/v2/guide/components-custom-events.html#%E8%87%AA%E5%AE%9A%E4%B9%89%E7%BB%84%E4%BB%B6%E7%9A%84-v-model"  //完整url
origin: "https://cn.vuejs.org"
pathname: "/v2/guide/components-custom-events.html"
port: "" // 端口
protocol: "https:"   //协议
search: "?q=123&page=1&type=note"  // 参数部分

window.screen // screen对象用于获取用户的屏幕信息

availHeight: 824 // 窗口可用高度
availLeft: 0
availTop: 0
availWidth: 1536 // 窗口可用宽度
colorDepth: 24
height: 864  // 屏幕高度
orientation: ScreenOrientation {angle: 0, type: "landscape-primary", onchange: null}
pixelDepth: 24
width: 1536  // 屏幕宽度



```

## DOM 文档对象模型

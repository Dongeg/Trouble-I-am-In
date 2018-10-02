# js 基础语法

## BOM 浏览器对象模型

```js
window.scrollTo(0,1000)  // 页面滚动到指定位置

window.history.length  // 历史页的数量

window.history.back() //上一页

window.history.forward() // 下一页

window.history.go(-1)

// https://cn.vuejs.org/v2/guide/components-custom-events.html#v-model

window.location

hash: "#v-model"  // 锚点
host: "cn.vuejs.org"  //  主机名+端口
hostname: "cn.vuejs.org"  // 主机名
href: "https://cn.vuejs.org/v2/guide/components-custom-events.html#v-model"  //完整url
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

```js

/* dom节点获取 */
document.getElementById('id');
document.getElementsByClassName('className') // ie9+
document.getElementsByName('name'); // 元素的 name 属性
document.getElementsByTagName('p') // 节点名
document.querySelector('.class') // 返回匹配指定选择器的第一个元素
document.querySelectorAll('.class') // 返回匹配指定选择器

elementNode.getAttribute(name) // 通过元素节点的属性名称获取属性的值

elementNode.setAttribute(name,value) // 增加一个指定名称和值的新属性，或者把一个现有的属性设定为指定的值


```

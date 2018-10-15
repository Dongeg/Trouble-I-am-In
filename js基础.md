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

window.devicePixelRatio  // 获取dpr






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

// 节点属性

elementNode.nodeName // 节点名称

1. 元素节点的 nodeName 与标签名相同
2. 属性节点的 nodeName 是属性的名称
3. 文本节点的 nodeName 永远是 #text
4. 文档节点的 nodeName 永远是 #document

elementNode.nodeValue // 节点值

1. 元素节点的 nodeValue 是 undefined 或 null
2. 文本节点的 nodeValue 是文本自身
3. 属性节点的 nodeValue 是属性的值

elementNode.nodeType // 节点类型

  元素          1
  属性          2
  文本          3
  注释          8
  文档          9

elementNode.childNodes // 访问子节点childNodes,

节点之间的空白符，在firefox、chrome、opera、safari浏览器是文本节点，ie不是

elementNode.firstChild  等同于 elementNode.childNodes[0]

elementNode.lastChild

elementNode.parentNode //获取指定节点的父节点,父节点只能有一个

nodeObject.nextSibling // 下一个节点

nodeObject.previousSibling  // 上一个节点 可能获取到空白文本节点

// 跳过空白文本节点
function get_nextSibling(n){
    var x=n.nextSibling;
    while (x && x.nodeType!=1){
        x=x.nextSibling;
    }
    return x;
}

elementNode.appendChild(newnode)  // 在指定节点的最后一个子节点列表之后添加一个新的子节点

    var otest = document.getElementById("test");
    var php=document.createElement("li");
    php.innerHTML="php";
    otest.appendChild(php)


elementNode.insertBefore(newnode)  // 可在已有的子节点前插入一个新的子节点。

nodeObject.removeChild(node) // 删除子节点

node.replaceChild (newnode,oldnew )  // replaceChild 实现子节点(对象)的替换。返回被替换对象的引用

    function replaceMessage(){ 
    var oldnode=document.getElementById("oldnode");
    var newnode=document.createElement("i");
    newnode.innerHTML="javascript";
    oldnode.parentNode.replaceChild(newnode,oldnode);
    }    

document.createElement(tagName) // createElement()方法可创建元素节点。此方法可返回一个 Element 对象

   var body = document.body; 
   var input = document.createElement("input");  
   input.type = "button";  
   input.value = "创建一个按钮";  
   body.appendChild(input);  
   
   
   
   var body= document.body;             
   var btn = document.createElement("input");  
   btn.setAttribute("type", "text");  
   btn.setAttribute("name", "q");  
   btn.setAttribute("value", "使用setAttribute");  
   btn.setAttribute("onclick", "javascript:alert('This is a text!');");       
   body.appendChild(btn);  
   
document.createTextNode(data) // document.createTextNode(data) 


// 浏览器窗口可视区域大小
winW=document.documentElement.clientWidth || document.body.clientWidth
winH=document.documentElement.clientHeight || document.body.clientHeight

//scrollHeight 是网页内容实际高度，可以小于 clientHeight
var w=document.documentElement.scrollWidth|| document.body.scrollWidth;
var h=document.documentElement.scrollHeight|| document.body.scrollHeight;

// 元素宽度和高度，包括混动条
nodeElement.offsetWidth

nodeElement.offsetHeight




这两个属性只能用于元素设置了overflow的css样式中。否者这两个属性没有任何意义。且overflow的值不能为visible，但可以为hidden,auto,scroll的之中，但是hidden最常见。

scrollLeft:往左滚动了多宽

scrollTop:往上滚了多高。






offsetLeft:距离窗口左边多宽 。

offsetTop:距离窗口顶部多高 。
```

date 相关

```js
// 时间戳转日期字符串

function timestampToTime(timestamp) {
        var date = new Date(timestamp * 1000);//时间戳为10位需*1000，时间戳为13位的话不需乘1000
        var Y = date.getFullYear() + '-';
        var M = (date.getMonth()+1 < 10 ? '0'+(date.getMonth()+1) : date.getMonth()+1) + '-';
        var D = date.getDate() + ' ';
        var h = date.getHours() + ':';
        var m = date.getMinutes() + ':';
        var s = date.getSeconds();
        return Y+M+D+h+m+s;
    }
    timestampToTime(1403058804);
    console.log(timestampToTime(1403058804));//2014-06-18 10:33:24

// 日期字符串转时间戳

var date = new Date('2014-04-23 18:55:49:123');
    // 有三种方式获取
    var time1 = date.getTime();
    var time2 = date.valueOf();
    var time3 = Date.parse(date);
    console.log(time1);//1398250549123
    console.log(time2);//1398250549123
    console.log(time3);//1398250549000
// 　第一、第二种：会精确到毫秒,第三种：只能精确到秒，毫秒用000替代    
```
// js 修改样式

```js
node.style.width = '15px';
node.style.cssText='width:15px'
```

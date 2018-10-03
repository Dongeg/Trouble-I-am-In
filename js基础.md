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


```

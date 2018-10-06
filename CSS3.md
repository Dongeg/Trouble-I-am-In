## 边框

```
border-radius:5px;
box-shadow: X轴偏移量 Y轴偏移量 [阴影模糊半径] [阴影扩展半径] [阴影颜色] [投影方式];
border-image:url(borderimg.png) 70 repeat
```

## 颜色

```
// 渐变色彩 
background-image:linear-gradient(to left, red, orange,yellow,green,blue,indigo,violet);

```

## 文字和字体

```
// div宽度不确定，超出...
text-overflow:ellipsis;
overflow:hidden;
white-space:nowrap;


// 如果想在第二行超出... 将 -webkit-line-clamp: 1;值改为2

.main{
  color: #333;
  font-weight: normal;
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 1;
  -webkit-box-orient: vertical;
}

## 加载服务端字体

@font-face {
    font-family : 字体名称;
    src : 字体文件在服务器上的相对或绝对路径;
}

@font-face{
    font-family: "MOOC Font";
    src: url("http://www.imooc.com/Amaranth-BoldItalic.otf");
}
.demo {
    font-family: "MOOC Font";
}

text-shadow: X-Offset Y-Offset blur color;

```

## 属性选择器

```
// 通配符

// class 以 icon 开头
a[class^=icon]{
  background: green;
  color:#fff;
}
// href属性以pdf结束
a[href$=pdf]{
  background: orange;
  color: #fff;
}
// title中包含more
a[title*=more]{
  background: blue;
  color: #fff;
}

ul > li:nth-child(2n){
  background:orange;
}
```


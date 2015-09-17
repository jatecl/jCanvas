这是一个简单易用的html5 canvas api。
## 初始化
```javascript
var stage = jCanvas.stage().resize(300, 200).appendTo(document.body);
jCanvas.image().src("demo.jpg").appendTo(stage);
```
## 通用属性
left: translate x
top: translate y
scale: scale
scaleX: scale x
scaleY: scale y
skew: skew
skewX: skew x
skewY: skew y
rotate: rotate in deg
```javascript
var stage = jCanvas.stage().resize(300, 200).appendTo(document.body);
jCanvas.image().src("demo.jpg").left(200).top(-100).scaleX(0.5).scaleY(0.6).skewX(20).skewY(10).rotate(100).appendTo(stage);
```
matrix: 当这个属性被设置后，之前的所有transform如left,top,scale将不再有效
opacity: opacity 0~1.在某些浏览器下opacity会有bug。
zIndex：z-index
shadowColor: 阴影颜色
shadowOffsetX: x方向阴影偏移
shadowOffsetY: y方向阴影偏移
shadowBlur: 阴影渐变长度
compositeOperation: 图层叠加算法。参考canvas的compositeOperation属性
```javascript
var stage = jCanvas.stage().resize(300, 200).appendTo(document.body);
jCanvas.image().src("demo.jpg").matrix([0.5,0,0,0.5,100,20]).appendTo(stage);
jCanvas.image().src("demo.jpg").zIndex(100).scale(0.2).left(30).top(30).shadowColor("red").shadowBlur(20).appendTo(stage);
//剪裁掉超出下面元素的部分
jCanvas.image().src("demo.jpg").zIndex(100).scale(0.3).left(10).top(10).compositeOperation("destination-in").appendTo(stage);
```
## 线框
线框包括了对象line, path, circle, rect, polygon
fill: 填充。渐变等填充方式没有提供快捷支持，还是需要调用原生方法来生成对象
stroke: 笔触填充。渐变等填充方式没有提供快捷支持，还是需要调用原生方法来生成对象
strokeWidth: 笔触宽度
lineCap: lineCap 参考canvas
lineJoin: lineJoin 参考canvas
miterLimit: miterLimit 参考canvas
```javascript
var stage = jCanvas.stage().resize(300, 200).appendTo(document.body);
jCanvas.rect().width(200).height(100).x(20).y(20).fill("red").stroke("green").strokeWidth(5).appendTo(stage);
```
### jCanvas.line、jCanvas.circle、jCanvas.rect
参考svg
### jCanvas.path
返回一个路径对象，参考svg的路径。使用path属性作为命令显示路径。部分兼容svg的路径表示方法（只支持大写，不支持H和V命令）
### jCanvas.polygon
返回一个线段对象
```javascript
var stage = jCanvas.stage().resize(300, 200).appendTo(document.body);
jCanvas.path().path("M20 20L200 100L100 150Z").fill("red").stroke("green").strokeWidth(5).appendTo(stage);
jCanvas.polygon().path([40, 40, 180, 80, 80, 130]).close(true).fill("red").stroke("green").strokeWidth(5).appendTo(stage);
```
## 其他
### jCanvas.group
分组对象，组合子对象，并统一变换
### jCanvas.image
位图
width: 宽度
height: 高度
src: 图片地址。可以直接设置Image对象
x: 图片x位置
y: 图片y位置
clipw: x方向 图片剪裁
cliph: y方向 图片剪裁
cx: x方向 图片剪裁位置
cy: y方向 图片剪裁位置
### jCanvas.text
文字
text
fontSize
fontWeight
fontStyle
fontFamily
lineHeight
fontVariant
textAlign
textBaseline
width
```javascript
var stage = jCanvas.stage().resize(300, 200).appendTo(document.body);
var group = jCanvas.group().left(150).top(100).rotate(10).appendTo(stage);
jCanvas.image().src("demo.jpg").x(-150).y(-100).width(300).height(200).appendTo(group);
jCanvas.text().text("Hello World").fontSize(36).textAlign("center").textBaseline("middle").fill("red").appendTo(group);
```
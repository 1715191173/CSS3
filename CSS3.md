# CSS3及CSS高级操作

#### 变量定义

```css
:root {
  /* 根目录下定义全局变量 */
  --变量名: 10px
}
  /* 使用 */
div {
  top: calc(var(--pointSize) * -2);
}
```

#### 边框和圆角

**圆角**：border-radius，可以分别设置四个角的弧度 **border-top(bottom)-left(right)-radius**
**阴影**：box-shadow: 横向阴影 纵向阴影 模糊程度 颜色（PS：文本阴影属性text-shadow） 
可以给边界设置图片，需要先设置 border: ..px solid transparent

#### 背景

background-origin：规定背景图片的**定位**区域(即设置图片坐标)
background-clip：规定背景区域的**显示区域**(全部显示/显示到边框/显示到内边距/仅显示内容区)
background-size：规定背景图片的**尺寸**

#### 渐变



#### 装饰性三角形

```css
  /* 规则三角形版本 */
.box2 {
  width: 0;
  height: 0;
  /* 下两行代码兼容低版本浏览器 */
  line-height: 0;
  font-size: 0;
  /* 通过边框调整大小 */
  border: 10px solid transparent;
  border-bottom-color: pink;
}

 /* 不规三角形版本 */
.box3 {
	width: 0;
  height: 0;
  border-color: transparent transparent transparent mediumslateblue ;
  border-style: solid;
  /* 以下参数决定三角形形态 */
  border-width: 22px 0 0 11px;
}
```



#### 对齐属性 vertical-align

用于设置图片或者表单（行内块元素）和文字 **垂直对齐**

⭐ 但是这样也会引起一些问题，例如图片底部默认空白缝隙问题。
	   解决：给图片添加vertical-align: bottom | top | bottom



#### Margin负值的应用

用于给多个盒子加边框

```css
ul li {
  float: left;
  list-style: none;
  width: 150px;
  height: 200px;
  border: 1px solid slateblue;
  margin-left: -1px;
}

ul li:hover {
  /* 方法一 当盒子没有定位*/
  position: relative;
  border: 1px solid salmon;

  /* 方法二 盒子有定位*/
  z-index: 1;
  border: 1px solid salmon;
}
```



#### 行内块元素应用

```css
.box {
  text-align: center;
}
.box a {
  display: inline-block;
  width: 36px;
  height: 36px;
  --width: 36px;
  background-color: #f7f7f7;
  border: 1px solid #ccc;
  text-align: center;
  line-height: var(--width);
  text-decoration: none;
  color: #333333;
}

<div>
	<a href="#">1</a>
</div>
```



#### 属性选择器

E[att]              选择具有att属性的 E 元素
E[att="val"]    选择具有att属性且属性值等于val的 E 元素(实际应用中没有双引号)
E[att^="val"]    选择具有att属性且值以val开头的 E 元素(实际应用中没有双引号)
E[att$="val"]    选择具有att属性且值以val结尾的 E 元素(实际应用中没有双引号)
E[att*="val"]    选择具有att属性且值含有val的 E 元素(实际应用中没有双引号)



#### 结构伪类选择器

E:first-child          匹配父元素中的第一个子元素 E
E:last-child           匹配父元素中的最后一个子元素 E
E:nth-child(n)       匹配父元素中第 n 个子元素 E (⭐ 先排序号查找再匹配是否为元素 E)
⭐ n可以是even(偶数)/odd(奇数) 也可以是公式，如果是公式则从0开始计算，第0个元素或超出元素的会被忽略
E:first-of -type     指定类型E的第一个
E:last-of -type      指定类型E的最后一个
E:nth-of-type(n)   指定类型E的第 n 个 (⭐ 先匹配是否为元素 E 再按顺序查找)



#### 伪元素选择器

用于简化HTML结构

```css
/* 相当于为某元素创建一个子行内元素 */
div::before{
	content: 'hhhhh'
}

div::after{
  ...
}
```


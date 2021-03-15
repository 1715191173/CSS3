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



#### CSS3盒子模型

CSS3中通过 **box-sizing** 来指定盒模型，其值可以为content-box(默认)或者是border-box

content-box 盒子大小为 width + padding + border（以前默认）
border-box 盒子大小为 width 	⭐在这个模型下，我们更改padding和border就不会成撑大盒子



#### CSS3滤镜 filter

语法：filter: 函数();



#### CSS3新增过渡属性

语法：transition: 要过渡的属性 花费的时间 运动曲线 何时开始, ... ;



#### 2D转换

​	**平移变换**

```css
transform: translate(x, y)
/* 分开写法 */
transform: translateX(n)
transform: translateY(n)
```

​	**利用平移变换居中元素**

```css
div {
	position: relative;
  width: 500px;
  height: 500px;
  background-color: #87ceeb;
}

p {
	position: absolute;
  top: 50%;
  left: 50%;
  width: 200px;
  height: 200px;
  background-color: mediumslateblue;
}
```

transform属性参数可以是 % 移动的距离是参照自身宽度和高度

​	**旋转变换**

```css
transform: rotate(...deg) 
/* 其单位也可以是turn 代表圈数 */
```

​	**更改中心点**

```css
transform-origin: x y;
```

​	**缩放**

```css
transform: scale(x, y)
```



**综合写法**

```css
transform: translate() rotate() scale() ...
```

⭐ 其顺序会影响转换的效果(先旋转会改变坐标方向)，**所以，当我们同时有位移和其他属性的时候，记得将位移放在最前**



#### CSS3动画

**步骤**

1. 用 keyframe 定义动画（类似定义类选择器） 

   ```css
   @keyframe 动画名称 {
   	0% {
   		width: 100px;
   	}
   	100% {
   		width: 200px;
   	}
   }
   @keyframe 动画名称 {
   	from {
   		width: 100px;
   	}
   	to {
   		width: 200px;
   	}
   }
   ```

   

2. 调用动画

   ```css
   /* 在需要用到动画的元素中加入以下属性 */
   animation-name: 动画名称;
   animation-duration: 2s;
   ```



其他一些重要属性：

1. animation-timing-function -> 运动速度曲线
2. animation-delay -> 动画何时开始
3. animation-iteration-count -> 规定动画播放次数，默认是1，还有infinite
4. animation-direction -> 规定动画是否在下一周期逆向播放，默认"normal"，alternate逆播放【通常与animation-iteration-count连用】
5. animation-fill-mode -> 规定动画结束后状态，forwards保持，回到起始backwards



**简写**（用于调用动画）

```css
animation: name duration steps(n) timing-function delay iteration-count direction fill-mode
```





#### CSS3 3D

三维坐标系： x水平向右，y垂直向下，z垂直屏幕往外

```css
transform: tanslate3d(x, y, z)
/* 通常z方向单位是 px */
```



##### **透视 perspective**

透视写在被观察元素的父盒子上面
d：视距，人的眼睛到屏幕的距离
z：z轴 物体距离屏幕的距离
👀\_\_\_d\_\_\_屏幕\_\_\_z\_\_\_🔺 



##### 3D旋转

遵循 **左手准则**

```
/* 沿x轴旋转...角度 */
transform: rotateX(...deg) 

/* 沿自定义轴旋转...角度 此处x,y,z均为矢量*/
transform: rorate3d(x, y, z, ...deg)
```



##### ⭐3D呈现 transform-style

- 控制子元素是否开启三维立体环境
- 属性值为 flat 默认值，子元素不开启3D立体空间；preserve-3d，子元素开启3D立体空间
- 代码写给父级，但是影响子元素


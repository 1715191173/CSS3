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
```



#### 对齐属性 vertical-align

用于设置图片或者表单（行内块元素）和文字 **垂直对齐**

⭐ 但是这样也会引起一些问题，例如图片底部默认空白缝隙问题。
	   解决：给图片添加vertical-align: bottom | top | bottom


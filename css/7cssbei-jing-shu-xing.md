## 背景 {#背景}

CSS中提供了为元素设定背景的功能，我们看到许多设计精良的网页，在很大程度上是灵活运用CSS背景实现装饰效果的。在CSS中，不但可以为整个网页设定背景，也可为具体元素设定背景，任何可显示出来的元素都可以设定背景样式。

### 设置背景色 {#设置背景色}

CSS通过background-color属性为元素设定背景颜色，颜色值的设定同color属性。background-color属性的默认值为transparent（透明）。如下例中的规则将使段落中的内容颜色为黑色，段落的整体背景色为浅灰色。

```css
p {
    background-color: #eee;
    color: black;
}
```

### 设置背景图片 {#设置背景图片}

一般情况下，我们会认为色块过于单调，缺少变化，因此，我们可以使用CSS提供的图像背景来装饰页面。在CSS中和图像背景有关的属性有：

1. **background-image**
   用来指定作为背景使用的图片所在的地址，它的值为URL地址或者渐变色，默认值为none。此外，当同时定义了背景颜色和背景图像时，背景图像覆盖在背景颜色之上。
2. **background-repeat**
   来设定背景图片的重复方式，background-repeat的值有：repeat（沿水平和垂直方向平铺）、repeat-x（沿水平方向平铺）、repeat-y（沿垂直方向平铺）或者no-repeat（不平铺显示），默认值为repeat。
3. **background-position**
   用来设定背景图像的位置，位置信息有两个，第一个用来指定横向坐标，第二个用来指定纵向坐标。坐标的表示可以使用百分数、带单位的长度以及关键字（left、center、right、top、middle、bottom），默认值为0。
4. **background-attachment**
   用来设定背景图像的滚动模式。值有三个，其中scroll表示背景图像会随着页面窗口滚动；fix表示固定在窗口，不随其滚动；local表示元素随元素滚动时背景图像也会跟着滚动，因为背景图像总是要跟着内容。local值是CSS3新增的值。background-attachment默认值为scroll。

例如：

```css

div#footer {
    background-image: url(bg.png);
    background-repeat: no-repeat;
    background-attachment: scroll;
    background-position: center bottom;
}
```

上述规则为id等于footer的div元素指定背景图像，背景图像的来源为当前网页同级目录中的bg.png文件，该图片在元素背景范围内部重复，并且随网页滚动，图片的出现在div元素背景范围内居中靠下的位置。

其中，background-position 属性，可以使用top、right、bottom、left和center关键字以及像素、百分比或者其他长度单位。CSS 在定位时，坐标原点位于左上角，如下图所示：

![](https://yangjh.gitee.io/front-end/images/background-position.png "background坐标体系")

通常情况下，我们将background-color、 background-image、 background-position、和 background-repeat 属性简写到background属性中。简写时，属性的顺序有多种，普遍采用 background-color、 background-image、 background-position、和 background-repeat的顺序。 例如：

```css

div {
  background: #b2b2b2 url("alert.png") 20px 10px no-repeat;
}
```

### 设置线性渐变背景 {#设置线性渐变背景}

许多年以来，设计师和开发人员若要实现背景渐变效果，只能使用图像处理软件制作渐变背景图片。但在CSS3中，我们现在可以使用渐变背景属性来代替以往繁琐的做法，只需一条语句，就可以实现漂亮的渐变背景效果。

CSS的线性渐变背景是在 background 或者 background-image 属性中使用linear-gradient\(\)函数实现，例如：

```
div {
  background: #466368;
  background: linear-gradient(#648880, #293f50);
}
```

linear-gradient\(\)函数必须包括至少两个值，第一个值为渐变起始值，第二个值为渐变结束值，浏览器会计算并平滑渲染出介于这两个颜色值之间的内容。

在渐变色背景之前，我们还声明了背景色，这样做的目的是当浏览器不支持渐变色属性时，使用指定的背景色作为背景。

默认情况下，线性渐变的方向为从上至下，我们可以在颜色值之前，使用关键词或者角度来改变渐变的方向。例如：

```css

div {
  background: #466368;
  background: linear-gradient(to right bottom, #648880, #293f50);
}
```

上例中，我们生成了一个从左上角渐变到右下角的渐变填充背景。

除了使用关键字之外，还可以使用角度，例如，如果我们想要生成和上例类似的渐变填充，可以使用135deg调整渐变角度：

```
.deg {
    background: #466368;
    background: linear-gradient(135deg, black, white);
    border-radius: 6px;
    height: 120px;
}
```

### 设置径向渐变 {#设置径向渐变}

线性渐变非常适合从不同方向之间的渐变，不过有时候，我们还需要径向渐变。径向渐变使用radial-gradient\(\)，其他类似于线性渐变。例如：

```css

div {
  background: #466368;
  background: radial-gradient(#648880, #293f50);
}
```

### 使用多个色标 {#使用多个色标}

要实现渐变效果，最少需要两个颜色值。但我们还可以使用多个色标，生成不同颜色值之间的渐变效果，不同颜色值会在指定的方向上平均分布，如：

```css

div {
  background: #648880;
  background: linear-gradient(to right, #f6f1d3, #648880, #293f50);
}
```

对于新手而言，手工生成复杂的渐变效果还是比较困难的，幸运的是，网络上有很多可以在线生成渐变效果的工具，如[CSS3 gradient generators](http://www.cssmatic.com/gradient-generator)，借助于这些工具，新手可以学习复杂渐变的生成代码。


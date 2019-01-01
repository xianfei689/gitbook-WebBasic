## 盒模型 {#盒模型}

在理解CSS是如何控制页面显示效果的时候，我们必须要掌握盒模型（Box Model）和定位（position）机制。CSS借助于盒模型和定位机制，结合文档树，能够精确、高效地控制内容在页面中的位置，从而实现页面的布局。

### 盒模型的概念 {#盒模型的概念}

所有HTML元素，在页面的呈现过程中，都遵循CSS制定的盒模型（Box Model），盒模型是一个包含外边距、边框线、内边距以及内容的矩形容器。具体如下图所示：[\[14\]](https://yangjh.gitee.io/front-end/References.html#cite-14)

![](https://yangjh.gitee.io/front-end/images/box.png "盒模型")

从图中我们可以看到，元素的盒模型由外边距\(margin\)、边框线\(border\)、内边距（padding）以及元素的内容（content）构成，CSS对外边距、边框线、内边距的控制可以分方向进行，也可以整体控制，如上图中的TM就表示上侧外边距、LM表示左侧外边距、RM表示右侧外边距、BM表示底侧外边距。

在CSS中，直接用来描述盒模型的属性有margin、border、padding、width、height。 需要注意的是，CSS提供的宽度属性（width）和高度属性（height）指的是内容区域（content）的宽度和高度，而不是整个盒模型的宽度和高度。整个盒模型的大小应该包括内外边距及边框的宽度。

盒模型的宽度 = "margin-left" + "border-left" + "padding-left" + "width" + "padding-right" + "border-right" + "margin-right"

盒模型的高度 = "margin-top" + "border-top" + p"adding-top" + "height" + p"adding-bottem" + "border-bottom" + "margin-right"

### 设置盒子大小 {#设置盒子大小}

在CSS中，可以使用盒模型的width和height属性为除行内元素之外的大多数元素设置高度和宽度。行内元素的宽度和高度取决于自身内容。

宽度和高度的值可以为百分比、带单位的长度或者是auto。如：

```css
#content {
    width: 90%;
    height: 300px;
}
```

百分比的计算是按照父元素的大小来计算，而不是按照本身的大小。如果没有指定宽度，盒模型就是用默认值100\%，也就是说和所在容器的宽度一样，如果没有指定高度，浏览器则会根据内容自动计算出高度大小。

除了width和height之外，CSS还提供了max-height、max-width、min-height、min-width属性。

### 设置外边距 {#设置外边距}

外边距用来控制元素之间的距离，在CSS中，使用margin属性来控制外边距，外边距是透明的空间量。内容之间适当的空间能够增加内容的可读性。除行内元素不接受上下外边距的设定外，其他元素都可以设定外边距。

margin属性的值可以是带单位的长度、百分比和auto。设置外边距的方式如下：

```css

div {
    margin: 10px;
}
```

上述规则表示div元素四侧的外边距为10个像素。

```css

div {
    margin: 10px 20px;
}
```

上述规则表示div元素上下侧的外边距为10个像素，左右侧的外边距为20像素。

```css

div {
    margin: 10px 20px 5px;
}
```

上述规则表示div元素上侧的外边距为10像素，左右两侧的外边距为20像素，下侧的外边距为5像素。

```css

div {
    margin: 10px 20px 0 5px;
}
```

上述规则表示div元素上侧的外边距为10像素，右侧的外边距为20像素，下侧外边距为0，左侧外边距为5像素。

除了使用margin统一设定元素外边距外，CSS还提供了margin-top、margin-right、margin-bottom以及margin-left四个属性分别设定各侧的外边距。

需要特别说明的是，当元素左右两侧的外边距取值auto时，这个元素就会在所在容器中居中。如：

```css

div {
    margin: 0 auto;
}
```

### 设定内边距 {#设定内边距}

CSS中使用padding表示内边距，内边距和外边距在很多方面是相似的。padding的值可以是带单位的长度或者是百分比。padding属性值中没有auto。padding属性值可以是1-4个值，其意义与margin相同。padding也可以分侧指定，如padding-top、padding-right、padding-bottom、padding-left。

### 设置边框 {#设置边框}

边框是进行信息组织是的一种有效手段，通过边框的使用，能够区分不同类型的信息，而且边框还是一种装饰手段，能在组织信息的同时美化页面。CSS提供了border-style、border-width和border-color以及border元素来控制边框的样式、宽度以及颜色。如：

```css

#footer {
    border-style: dashed;
    border-width: 1px;
    border-color: #ccc;
}
```

上述规则将使得id为footer的元素四周拥有灰色、1个像素宽度的虚线边框。

其中border-style的属性值用来指定边框线的样式，默认值为none，也就是没有边框，因此，在定义边框属性时，border-style实际上是必须要指定的，常用的值有：solid, double, dashed, dotted, and none。

border-width的属性用来指定边框先的宽度，宽度值为带单位的长度（如 1px）或关键字（thin、medium、thick），宽度默认值为medium。

border-color属性用来指定边框颜色，其值可以为文本、16进制颜色值和rgb函数值，颜色的默认继承元素内容的颜色。

CSS还提供了快速设定边框样式的属性——border，如上述的样式可以这样简写：

```
#footer {
    border: dashed 1px #ccc;
}
```

border的值中必须要指定的是border-style，其他两个可以任意组合，并且对出现的先后顺序也无要求。和margin、padding属性类似，border-style、border-width以及border-color可以接受1-4个值，用以分别指定不同侧面的边框样式，如下面的样式规则使得id为footer的元素上下两侧没有边框，左右两侧的边框样式为虚线、宽度为medium、颜色和该元素的内容颜色一致：

```
#footer {
    border-style: none dashed;
}
```

最后，CSS也提供了分别指定不同方向上边框的机制：border-top、border-right、border-bottom以及border-left。如下面的样式规则将使得id为footer的元素拥有1个像素宽的红色虚线上边框：

```css

#footer {
    border-top: dashed 1px red;
}
```

### 圆角 {#圆角}

border-radius属性，允许我们为元素设置圆角效果。

border-radius属性接受长度单位，包括百分比和像素。border-radius如果只有一个值，则设定四个角，俩值、三个值和四个值的情况与margin、padding类似，都按顺时针方向设定。例如：

```css

.border-football {
  border-radius: 15px 75px;
}
```

上述代码设定左上、右下角为半径15像素的圆角，而右上和左下的圆角半径为75像素。


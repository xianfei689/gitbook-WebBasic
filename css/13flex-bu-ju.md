# 13、Flex 布局

![css-flexbox](https://yangjh.gitee.io/front-end/images/css-flexbox.png)

Flex box布局模型的主要目的是提供更有效率的布局方式，尤其是当容器内元素的尺寸不固定的时候更能表现出它的优势。它能够自动识别子元素的尺寸，从而为盒装模型提供更高的灵活性。

## 基本概念 <a id="&#x57FA;&#x672C;&#x6982;&#x5FF5;"></a>

如果元素采用Flex进行布局，那么这个元素就可以称为Flex容器（Flex container），元素的所有子元素称为Flex项目（Flex item）。

下图为Flexbox模型图：

![CSS3-Flexbox-Model](https://yangjh.gitee.io/front-end/images/CSS3-Flexbox-Model.jpg)

### 几个术语 <a id="&#x51E0;&#x4E2A;&#x672F;&#x8BED;"></a>

* main axis：水平主轴
* main-start：主轴开始位置，与边框的交叉点
* main-end：主轴的结束位置
* cross axis：垂直交叉轴
* cross-start：交叉轴的开始位置
* cross-end：交叉轴的结束位置
* main size：单个项目占据的主轴空间
* cross size：单个项目占据的交叉轴空间

### 浏览器兼容情况 <a id="&#x6D4F;&#x89C8;&#x5668;&#x517C;&#x5BB9;&#x60C5;&#x51B5;"></a>

![CSS flexbox](https://yangjh.gitee.io/front-end/images/flexbox-compatibility.png)

点击查看更多信息：[flexbox-compatibility](http://caniuse.com/#feat=flexbox)

## Flexbox容器的构造方法 <a id="flexbox&#x5BB9;&#x5668;&#x7684;&#x6784;&#x9020;&#x65B9;&#x6CD5;"></a>

1. 任何一个容器都可以指定为Flexbox布局：

```css
.flex-container {
  display: -webkit-flex; /* Safari */
  display: flex;
}
```

1. 行内元素可以指定Flexbox布局：

```css
.flex-container {
  display: -webkit-inline-flex; /* Safari */
  display: inline-flex;
}
```

**注意，设为 Flex 布局以后，子元素的**`float`**、**`clear`**和**`vertical-align`**属性将失效。**

## Flexbox容器特性 <a id="flexbox&#x5BB9;&#x5668;&#x7279;&#x6027;"></a>

### flex-direction属性 <a id="flex-direction&#x5C5E;&#x6027;"></a>

`flex-direction`属性决定主轴的方向（即项目的排列方向）。

```css
.flex-container {
  flex-direction: row | row-reverse | column | column-reverse;
}
```

#### Values: <a id="values"></a>

```css
.flex-container {
  -webkit-flex-direction: row; /* Safari */
  flex-direction:         row; /* 默认值 */
}
```

主轴为水平方向，起点在左端:

![CSS flexbox](https://yangjh.gitee.io/front-end/images/flex-direction-row.png)

```css
.flex-container {
  -webkit-flex-direction: row-reverse; /* Safari */
  flex-direction:         row-reverse;
}
```

主轴为水平方向，起点在右端:

![CSS flexbox](https://yangjh.gitee.io/front-end/images/flex-direction-row-reverse.png)

```css
.flex-container {
  -webkit-flex-direction: column; /* Safari */
  flex-direction:         column;
}
```

主轴为垂直方向，起点在上端:

![CSS flexbox](https://yangjh.gitee.io/front-end/images/flex-direction-column.png)

```css
.flex-container {
  -webkit-flex-direction: column-reverse; /* Safari */
  flex-direction:         column-reverse;
}
```

主轴为垂直方向，起点在下端:

![CSS flexbox](https://yangjh.gitee.io/front-end/images/flex-direction-column-reverse.png)

### flex-wrap属性 <a id="flex-wrap&#x5C5E;&#x6027;"></a>

`flex-wrap`属性决定内容在抽线上排列不下的换行方式。

```css
.flex-container {
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```

#### Values: <a id="values"></a>

```css
.flex-container {
  -webkit-flex-wrap: nowrap; /* Safari */
  flex-wrap:         nowrap; /* 默认 */
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/flex-wrap-nowrap.png)

设置不换行。

```css
.flex-container {
  -webkit-flex-wrap: wrap; /* Safari */
  flex-wrap:         wrap;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/flex-wrap-wrap.png)

设置自动换行，且第一行在上方。

```css
.flex-container {
  -webkit-flex-wrap: wrap-reverse; /* Safari */
  flex-wrap:         wrap-reverse;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/flex-wrap-wrap-reverse.png)

设置自动换行，且第一行在下方。

### flex-flow属性 <a id="flex-flow&#x5C5E;&#x6027;"></a>

`flex-flow`属性是`flex-direction`属性和`flex-wrap`属性的简写形式。

#### **Values:** <a id="values"></a>

```css
.flex-container {
  -webkit-flex-flow: <flex-direction> || <flex-wrap>; /* Safari */
  flex-flow:         <flex-direction> || <flex-wrap>;
}
```

默认属性值：

```css
.flex-container {
  -webkit-flex-flow: row nowrap; /* Safari */
  flex-flow:         row nowrap;
}
```

### justify-content属性 <a id="justify-content&#x5C5E;&#x6027;"></a>

`justify-content`属性定义项目在主轴上的对齐方式。

```css
.flex-container {
  justify-content: flex-start | flex-end | center | space-between | space-around;
}
```

#### Values: <a id="values"></a>

```css
.flex-container {
  -webkit-justify-content: flex-start; /* Safari */
  justify-content:         flex-start;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/justify-content-flex-start.png)左对齐。

```css
.flex-container {
  -webkit-justify-content: flex-end; /* Safari */
  justify-content:         flex-end;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/justify-content-flex-end.png)右对齐。

```css
.flex-container {
  -webkit-justify-content: center; /* Safari */
  justify-content:         center;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/justify-content-center.png)居中。

```css
.flex-container {
  -webkit-justify-content: space-between; /* Safari */
  justify-content:         space-between;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/justify-content-space-between.png)两端对齐，项目之间的间隔相等。

```css
.flex-container {
  -webkit-justify-content: space-around; /* Safari */
  justify-content:         space-around;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/justify-content-space-around.png)每个项目两侧的间隔相等。

### align-items属性 <a id="align-items&#x5C5E;&#x6027;"></a>

`align-items`属性定义项目在交叉轴上的对齐方式。

```css
.flex-container {
  align-items: align-items: flex-start | flex-end | center | baseline | stretch;
}
```

#### Values: <a id="values"></a>

```css
.flex-container {
  -webkit-align-items: flex-start; /* Safari */
  align-items:         flex-start;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/align-items-flex-start.png)交叉轴的起点对齐。

```css
.flex-container {
  -webkit-align-items: flex-end; /* Safari */
  align-items:         flex-end;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/align-items-flex-end.png)交叉轴的终点对齐。

```text
.flex-container {
  -webkit-align-items: center; /* Safari */
  align-items:         center;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/align-items-center.png)交叉轴的中点对齐。

```css
.flex-container {
  -webkit-align-items: baseline; /* Safari */
  align-items:         baseline;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/align-items-baseline.png)项目的第一行文字的基线对齐。

```css
.flex-container {
  -webkit-align-items: stretch; /* Safari */
  align-items:         stretch;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/align-items-stretch.png)如果项目未设置高度或设为auto，将占满整个容器的高度。

### align-content属性 <a id="align-content&#x5C5E;&#x6027;"></a>

`align-content`定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。

```css
.flex-container {
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}
```

#### Values: <a id="values"></a>

```css
.flex-container {
  -webkit-align-content: flex-start; /* Safari */
  align-content:         flex-start;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/align-content-flex-start.png)与交叉轴的起点对齐。

```css
.flex-container {
  -webkit-align-content: flex-end; /* Safari */
  align-content:         flex-end;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/align-content-flex-end.png)与交叉轴的终点对齐。

```css
.flex-container {
  -webkit-align-content: center; /* Safari */
  align-content:         center;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/align-content-center.png)与交叉轴的中点对齐。

```css
.flex-container {
  -webkit-align-content: space-between; /* Safari */
  align-content:         space-between;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/align-content-space-between.png)与交叉轴两端对齐，轴线之间的间隔平均分布。

```css
.flex-container {
  -webkit-align-content: space-around; /* Safari */
  align-content:         space-around;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/align-content-space-around.png)每根轴线两侧的间隔都相等。

```css
.flex-container {
  -webkit-align-content: stretch; /* Safari */
  align-content:         stretch;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/align-content-stretch.png)轴线占满整个交叉轴。

## Flexbox项目特性 <a id="flexbox&#x9879;&#x76EE;&#x7279;&#x6027;"></a>

### （一）order属性 <a id="&#xFF08;&#x4E00;&#xFF09;order&#x5C5E;&#x6027;"></a>

`order`属性定义项目的排列顺序。数值越小，排列越靠前，默认为`0`。

#### Values: <a id="values"></a>

```css
.flex-item {
  -webkit-order: <integer>; /* Safari */
  order:         <integer>;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/flex-order.png)

### flex-grow属性 <a id="flex-grow&#x5C5E;&#x6027;"></a>

`flex-grow`属性定义项目的放大比例，默认为`0`，即如果存在剩余空间，也不放大。

#### Values: <a id="values"></a>

```css
.flex-item {
  -webkit-flex-grow: <number>; /* Safari */
  flex-grow:         <number>;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/flex-grow.png)

如果所有项目的`flex-grow`属性都为`1`，则它们将等分剩余空间（如果有的话）。如果一个项目的`flex-grow`属性为`2`，其他项目都为`1`，则前者占据的剩余空间将比其他项多一倍。

### flex-shrink属性 <a id="flex-shrink&#x5C5E;&#x6027;"></a>

`flex-shrink`属性定义了项目的缩小比例，默认为`1`，即如果空间不足，该项目将缩小。

#### Values: <a id="values"></a>

```css
.flex-item {
  -webkit-flex-shrink: <number>; /* Safari */
  flex-shrink:         <number>;
}
```

![CSS flexbox](https://yangjh.gitee.io/front-end/images/flex-shrink.png)

如果所有项目的`flex-shrink`属性都为1，当空间不足时，都将等比例缩小。如果一个项目的`flex-shrink`属性为0，其他项目都为1，则空间不足时，前者不缩小。

负值对该属性无效。

### flex-basis属性 <a id="flex-basis&#x5C5E;&#x6027;"></a>

`flex-basis`属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为`auto`，即项目的本来大小。

#### Values： <a id="values&#xFF1A;"></a>

```css
.flex-item {
  -webkit-flex-basis: auto | <width>; /* Safari */
  flex-basis:         auto | <width>;
}
```

它可以设为跟`width`或`height`属性一样的值（比如350px），则项目将占据固定空间。

### flex属性 <a id="flex&#x5C5E;&#x6027;"></a>

`flex`属性是`flex-grow`,`flex-shrink`和`flex-basis`的简写，默认值为`0 1 auto`。后两个属性可选。

#### Values： <a id="values&#xFF1A;"></a>

```css
.flex-item {
  -webkit-flex: none | auto | [ <flex-grow> <flex-shrink>? || <flex-basis> ]; /* Safari */
  flex:         none | auto | [ <flex-grow> <flex-shrink>? || <flex-basis> ];
}
```

### align-self属性 <a id="align-self&#x5C5E;&#x6027;"></a>

`align-self`属性允许单个项目有与其他项目不一样的对齐方式，可覆盖`align-items`属性。默认值为`auto`，表示继承父元素的`align-items`属性，如果没有父元素，则等同于`stretch`。

#### Values： <a id="values&#xFF1A;"></a>

```css
.flex-item {
  -webkit-align-self: auto | flex-start | flex-end | center | baseline | stretch; /* Safari */
  align-self:         auto | flex-start | flex-end | center | baseline | stretch;
}}
```

## 参考信息： <a id="&#x53C2;&#x8003;&#x4FE1;&#x606F;&#xFF1A;"></a>

1. [https://www.w3.org/html/ig/zh/css-flex-1/\#intro](https://www.w3.org/html/ig/zh/css-flex-1/#intro)
2. [http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html\)](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
3. [https://scotch.io/tutorials/a-visual-guide-to-css3-flexbox-properties](https://scotch.io/tutorials/a-visual-guide-to-css3-flexbox-properties)
4. [https://css-tricks.com/snippets/css/a-guide-to-flexbox/](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
5. [https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS\_layout/Flexbox](https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Flexbox)


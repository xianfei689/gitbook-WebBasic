## 定位及布局 {#定位及布局}

### 信息流 {#信息流}

浏览器在呈现信息时会按照元素的类型进行处理，它将块元素从上到下显示（块元素与块元素之间另起一行），将行内元素按语言方向水平显示（如汉字、英语是从左到右，维吾尔语、阿拉伯语等有些语言是从右到左），行内元素直到到达容器边缘时才换行显示，这种显示元素的方式叫做页面的正常流。

常见的大多数元素属于块元素，如p、table、div、li、ul、ol、object、h1-h6等等，行内元素有a、span、img、b、strong等等。需要注意的是，匿名内容（即没有使用元素标签标注的内容）也按行内元素处理。

### display {#display}

元素如何显示，可以通过display属性进行指定。每一个元素都有一个默认的display属性，但这个属性值可以修改。块元素和行内元素可通过display属性改变它们的显示方式，比如在某些情景，编辑人员需要给行内元素添加高度，以改进元素的显示效果，行内元素是无法直接通过width属性指定高度的，但可以通过display属性将其变为块元素，再为其添加高度。

display有很多属性值，最常用的是block、inline、inline-block以及none。其中block将元素按照块元素方式显示；inline将元素按照行内元素显示；而inline-block模式将使元素像行内元素那样显示，但同时又具有bolock元素的特征，可以赋予宽度和高度等等；none模式将元素整体隐藏起来，相当于该元素不存在一样，元素一旦声明其display的值为none，包含在内部的内容及其后代元素都会隐藏，并且其内容和后代不能再通过display改变显示方式。

### 浮动 {#浮动}

除了相对定位和绝对定位能控制元素在正常流的位置之外，CSS还提供了浮动（float）机制来控制元素在正常流中的位置，在实际工作中，float属性是主要的定位、排版手段。从页面栏目的划分到图片的定位，大都通过float属性实现。

浮动的值有left、right和none，其中左浮动将会使得块元素浮动向所在父元素的左侧，其后续的内容将出现在该元素的右侧，并和该元素的顶端对齐。右浮动刚好相反，none则没有浮动效果。

先看一段HTML代码：

```php
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8" />
<title>浮动</title>
<style>
#head {
    border:1px #CCC solid;
    width:410px;
    height:100px;
    margin-bottom:10px;
}
#main {
    border:1px #CCC solid;
    width:400px;
    height:200px;
    margin-bottom:10px;
    padding:5px;
}
#left {
    border:1px #CCC solid;
    width:198px;
    height:198px;
}
#right {
    border:1px #CCC solid;
    width:193px;
    height:198px;
    margin-left:5px;
}
</style>
</head>
<body>
<div id="head">头部</div>
<div id="main">
  <div id="left">左侧</div>
  <div id="right">右侧</div>
</div>
</body>
</html>
```



